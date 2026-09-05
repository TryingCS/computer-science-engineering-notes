---
{"dg-publish":true,"permalink":"/extras/","dg-note-properties":{}}
---



---

#html 
## Block vs Inline

Imagine a page is a **column of text flowing top to bottom**.

**Block** elements say: *"I demand my own line. Give me the full width."*


Block examples you'll use: `<div>`, `<p>`, `<h1>`–`<h6>`, `<ul>`, `<li>`, `<header>`, `<nav>`, `<main>`, `<footer>`, `<section>`, `<form>`, `<table>`

**Inline** elements say: *"I'll just sit right here in the middle of the sentence. I only take the space I need."*

```html
<p>Status: <span>Active</span> since 2024</p>
```

The `<span>` doesn't push anything to a new line. It sits inside the sentence. It's like **highlighting a word** with a marker.

Inline examples: `<span>`, `<a>`, `<strong>`, `<em>`, `<img>`, `<input>`


> ⚠️ **Heads-up:** CSS can override all of this. You can make a `<span>` behave like a block or a `<div>` sit inline. The block/inline thing is just the **default** behaviour before CSS touches it. You'll deal with that in your CSS chat.

---

## Are `<ul>` and `<ol>` just visual?

Mostly yes, but with a small semantic difference:

- `<ul>` (unordered) → "these items are a group, order doesn't matter." Default look: bullet points.
- `<ol>` (ordered) → "these items are in a specific sequence." Default look: 1, 2, 3…

For a nav menu you use `<ul>` because "Dashboard, Students, Courses" isn't a ranked sequence. For a recipe's steps you'd use `<ol>` because step 1 must come before step 2.

And yes, CSS can remove the bullets/numbers entirely. So in the final styled app, the user might not even see them. But the semantic meaning stays for screen readers and search engines.

---

## Reuse the skeleton across pages?

**In pure HTML :** you just… copy-paste. You make `index.html`, `students.html`, `courses.html`, `login.html`, etc. Each one has the same header/nav/footer, and you change what's inside `<main>`.

I it's the reality of static HTML.

**Later, when you add a backend** (Node, Python, PHP…), you'll learn **templating**: you write the skeleton **once** in a template file, and the server injects the unique `<main>` content per page. You'll hit that when you get there. No need to worry about it now.

> ⚠️ **Heads-up:** There's also a JS approach called "Single Page App"

### one file per page the only way?

For a multi-page app in pure HTML: **yes, it's the standard and practical way.** 

**Rule of thumb:** one `.html` file per page. Copy the skeleton. Change `<main>`. Done.

---
[[forms\|next]]

