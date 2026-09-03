---
{"dg-publish":true,"permalink":"/z-misc/vercel-serverless-functions/","dg-note-properties":{}}
---

#backend
It is not only “time critical.” It is a deeper architecture issue.

A serverless function is designed like this:

```txt
Request comes in
Function runs
Function returns response
Function dies/sleeps
```

It is not designed to stay alive and hold things in memory.

A normal server is designed like this:

```txt
Server starts
It stays alive
It keeps connections/state/memory open
It responds whenever needed
```

That difference is the real issue.

---

## Simple example

### Serverless function

Like a vending machine:

> You press a button, it gives one result, then it waits for the next button press.

### Always-on server

Like a person standing in a room:

> They can remember things, watch a door, hold a conversation, and react instantly.

---

# Why live chat is hard with plain serverless

Real-time chat usually uses WebSockets or long-lived connections.

A WebSocket connection means:

```txt
User connects
Connection stays open
Server can push messages anytime
```

Example:

```txt
Alice connects
Bob connects
Alice sends message
Server instantly pushes it to Bob
```

The server needs to remember:

- Who is connected
- Which socket belongs to which user
- Which rooms/channels exist
- Who should receive what

But a serverless function usually cannot keep that connection open forever.

It may start when Alice sends a message, but it does not naturally stay alive and hold Bob’s connection too.

So the problem is not just:

> “It may be slow because it slept.”

The bigger problem is:

> “There is no permanent process holding all live connections and chat state.”

---

# Can simple chat still work with serverless?

Yes, sometimes.

For very basic hobby chat, you can use:

## 1. Polling

Frontend asks:

```txt
Any new messages?
Any new messages?
Any new messages?
```

Every few seconds.

This can work with serverless.

Downsides:

- Less instant 
- More requests
- More battery/network usage
- Feels less smooth

## 2. Managed realtime service

Use something made for realtime:

- Supabase Realtime
- Firebase
- Ably
- Pusher
- Cloudflare Durable Objects

Then Vercel can still host the app, but the realtime part is handled elsewhere.

---

# Why heavy media processing is hard

Example:

```txt
User uploads video
Server converts video
Takes 5 minutes
```

A serverless function usually has a timeout.

It may be killed after:

```txt
10 seconds
30 seconds
60 seconds
```

depending on platform/plan.

So if the job needs 5 minutes, plain serverless is a bad fit.

Again, the issue is not only performance.

It is this:

> Serverless functions are meant to finish quickly.  
> Long jobs need workers that are allowed to run for a long time.

---

# What “server must stay awake forever” really means

It does not always mean the app must be busy forever.

It means the process needs to exist continuously.

Examples:

## 1. WebSocket server

Needs to keep user connections open.

Example:

```txt
Chat app
Live collaboration
Multiplayer game
Live cursor sharing
```

## 2. Game server

Needs to keep game state in memory.

Example:

```txt
Player positions
Health
Inventory
Room state
```

If the function dies, the game state disappears.

## 3. Discord/Telegram bot

Some bots can work with webhooks, which can be serverless.

But bots using long polling usually need an always-on process.

Example:

```txt
Bot continuously checks:
"Any new messages for me?"
```

That needs a running process.

## 4. Background worker

Example:

```txt
Send 1000 emails slowly
Process uploaded files
Generate PDFs
Resize images
Sync data every minute
```

These need workers.

Serverless can trigger them, but not always do the long work itself.

## 5. Scheduled jobs/cron jobs

Example:

```txt
Every 5 minutes:
Check expired accounts
Send reminders
Clean database
```

Some platforms have cron features, but a pure serverless model does not naturally “wake itself up” without a scheduler.

## 6. Live audio/video streaming

Example:

```txt
User goes live
Server receives stream
Server forwards stream to viewers
```

That needs persistent connections and often specialized media servers.

## 7. IoT / MQTT

Example:

```txt
Devices stay connected
Server receives sensor data
Server sends commands
```

Usually needs persistent connection infrastructure.

---

# The deeper reason

Serverless functions are usually:

```txt
Stateless
Short-lived
Request-based
Temporary
```

They are great for:

```txt
Request -> do small job -> response
```

They are bad for:

```txt
Stay alive -> remember state -> keep connections -> push updates
```

So the issue is not only:

> “Cold starts are inconvenient.”

The issue is:

> “The serverless function may not exist long enough to do the job.”

---

# Example: chat with serverless

Imagine:

```txt
Alice opens chat
Bob opens chat
```

With a normal server:

```txt
Server keeps both connections open
Alice sends message
Server immediately sends to Bob
```

With basic serverless:

```txt
Alice sends message
Function wakes up
Saves message to database
Function dies
```

Bob may not know there is a new message until his app asks again.

So you need either:

```txt
Polling
```

or

```txt
A realtime service
```

or

```txt
An always-on WebSocket server
```

---

# Example: video processing

With serverless only:

```txt
User uploads video
Function starts processing
Function gets killed after timeout
```

Bad.

Better:

```txt
User uploads video to storage
Storage/service triggers a worker
Worker processes video
User checks status later
```

Or use a managed API.

---

# So what can’t Vercel serverless do well?

Mainly these patterns:

```txt
Long-running tasks
Persistent connections
Shared in-memory state
Continuous listening
Heavy CPU jobs
Background workers
Real-time game servers
Live streaming servers
Always-on bots
```

---

# What can Vercel serverless do well?

```txt
Login/signup
Saving posts
Fetching data
Handling forms
Calling external APIs
Webhooks
Small database queries
Redirects
Authentication checks
Simple CRUD apps
```

CRUD means:

```txt
Create
Read
Update
Delete
```

Most beginner full-stack apps are mostly CRUD.

Those work well on Vercel.

---

# Simple rule

If the backend only reacts to user actions:

```txt
User clicks button
Backend does quick work
Returns result
```

Serverless is usually fine.

If the backend must continuously exist:

```txt
Keep connections open
Remember live state
Run long jobs
Listen constantly
Push updates by itself
```

Then you need something beyond plain serverless.

---

# For hobby projects

For most beginner apps, you will be fine with:

```txt
Vercel + Supabase
```

or:

```txt
Vercel + Neon
```

Examples:

- Todo app
- Notes app
- Blog
- Bookmark app
- Expense tracker
- Habit tracker
- Simple social feed
- Contact form
- Auth app

If you later want:

- Real chat
- Multiplayer
- Live collaboration
- Bots
- Video processing

Then you add another service or use a normal server/worker.