---
{"dg-publish":true,"permalink":"/assets/subjects/z-misc/neon/","dg-note-properties":{}}
---

#misc 

### 1. The 100 Project Limit on Neon: Active vs. Lifetime
The 100-project limit is a **concurrent limit** (how many exist on your account at one time), **not** a lifetime cap. 
* You can create, run, and pause up to 100 projects simultaneously [[8\|8]]. 
* If you delete a project (which frees up a slot after 7 days [[2\|2]]), you can create a brand new one in its place. Community discussions confirm that deleting old projects allows you to "get below the limit" and continue creating new ones indefinitely [[5\|5]].

---

### 2. Is Supabase Still "Beefier" than Neon?
**Yes.** While Neon is an incredible standalone Postgres service that has recently bolted on Auth and Storage, Supabase is still a much more cohesive "Backend-as-a-Service" (BaaS) platform [[21\|21]]. Supabase was built from day one to be a Firebase alternative; Neon was built to be the best serverless Postgres and is only now expanding into other features [[19\|19]].

Here is how the features stack up side-by-side:

#### 🔴 Realtime (Winner: Supabase)
* **Supabase:** Has a native, built-in "Realtime" engine. You can listen to database changes (INSERT, UPDATE, DELETE) or broadcast messages via WebSockets straight out of the box.
* **Neon:** Does **not** have a built-in Realtime WebSocket service. If you want realtime updates in Neon, you have to build and host your own WebSocket server using "Neon Functions" or a third-party tool [[27\|27]]. 

#### 🟢 Database Branching (Winner: Neon)
* **Neon:** This is their superpower. You can instantly "branch" your database like a Git repository (e.g., create a "dev" branch from "main" in one second) [[11\|11]]. Neon recently made its Auth and Object Storage "branch-aware" as well.
* **Supabase:** Added branching recently, but Neon’s implementation is deeper, faster, and more central to the developer experience.

#### 🟡 Authentication (Tie, different philosophies)
* **Supabase Auth:** A mature, standalone Go-based service. It supports MFA, SSO, and phone auth. However, the users live in Supabase's internal `auth` schema, which makes them hard to query or join with your app's data via SQL.
* **Neon Auth:** A newer wrapper around an open-source library called "Better Auth." The cool part? Neon stores your users **directly in your own Postgres database** [[3\|3]]. You can write standard SQL `JOIN` queries between your `users` table and your `posts` table.

#### 🟡 File Storage (Tie)
* Both now offer S3-compatible Object Storage with Row-Level Security (RLS). Neon's is newer (launched in 2026), but it works seamlessly alongside their branching features. Supabase's storage is older and battle-tested.

#### 🔴 Edge Functions (Different Use Cases)
* **Supabase:** Uses Deno to run TypeScript functions at the **Edge** (globally distributed, very close to your users).
* **Neon:** Uses Node.js functions that run in the **same region** as your database. This means they aren't globally distributed, but they have near-zero latency when talking to your database.

---

### The Verdict
* **Choose Supabase** if you want a "batteries-included" experience where Auth, Realtime WebSockets, Storage, and Database are all managed perfectly in one dashboard, and you want to use the Schema hack to bypass the 3-project limit.
* **Choose Neon** if your projects are primarily database-driven (CRUD), you love SQL, you want to join user data directly, and you want to spin up hundreds of isolated database environments without hacking around a single Supabase instance.