---
{"dg-publish":true,"permalink":"/layout/","dg-note-properties":{}}
---


#html 

Before you build forms and tables, you need a **page skeleton** — where does the nav go, where does the content go, where does the footer go.

---

## Semantic layout tags

HTML5 gives you named containers so your structure reads like a description instead of a pile of `<div>`s:

```html
<body>

  <header>
    <h1>College Manager</h1>
  </header>

  <nav>
    <a href="/dashboard">Dashboard</a>
    <a href="/students">Students</a>
    <a href="/courses">Courses</a>
    <a href="/login">Login</a>
  </nav>

  <main>
    <h2>Dashboard</h2>
    <p>Welcome, Admin.</p>
    <!-- your forms, tables, CRUD stuff will live here -->
  </main>

  <footer>
    <p>&copy; 2026 College Manager</p>
  </footer>

</body>
```

| Tag | Role |
|---|---|
| `<header>` | Top banner. App name, logo. |
| `<nav>` | Navigation links. Sidebar or top bar. |
| `<main>` | **The actual page content.** One per page. |
| `<footer>` | Bottom. Copyright, contact. |

There's also `<section>` and `<aside>` you can nest inside `<main>` when a page gets complex:

```html
<main>
  <section>
    <h2>Student List</h2>
    <!-- table goes here later -->
  </section>

  <aside>
    <h3>Filters</h3>
    <!-- filter controls later -->
  </aside>
</main>
```

> ⚠️ **Heads-up:** These tags give you **zero visual styling** by default. `<header>` doesn't automatically stick to the top. `<nav>` doesn't automatically become a sidebar. That's all CSS. For now they just **label** regions so your HTML is readable.

---

## Lists for navigation

Your nav links will usually live in a list:

```html
<nav>
  <ul>
    <li><a href="/dashboard">Dashboard</a></li>
    <li><a href="/students">Students</a></li>
    <li><a href="/courses">Courses</a></li>
    <li><a href="/users">Users</a></li>
  </ul>
</nav>
```

- `<ul>` = unordered list (bullet points by default)
- `<ol>` = ordered list (numbered)
- `<li>` = list item (lives inside `<ul>` or `<ol>`)

You'll use `<ul>` for nav menus and `<ol>` for things like step-by-step instructions.

---

## `<div>` and `<span>`: the generic containers

Sometimes you just need a box with no semantic meaning:

```html
<div class="card">
  <p>Student name: Sara</p>
</div>
```

- `<div>` → generic **block** container (takes full width, starts on new line)
- `<span>` → generic **inline** container (wraps around a word/phrase, stays in the line)

```html
<p>Status: <span class="active">Active</span></p>
```

You'll use `<div>` a lot for grouping form fields, wrapping table sections, etc. `<span>` less often.

> ⚠️ **Heads-up:** `class="card"` and `class="active"` do **nothing** in HTML alone. They're hooks for CSS and JS to grab. You'll use them constantly in your CSS/JS chats. For now just know: `class` is a label you stick on an element so you can target it later.

---

## CRUD app skeleton

This is the actual structure you'll reuse on **every page** of your app 

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>College Manager</title>
</head>
<body>

  <header>
    <h1>College Manager</h1>
  </header>

  <nav>
    <ul>
      <li><a href="/dashboard">Dashboard</a></li>
      <li><a href="/students">Students</a></li>
      <li><a href="/courses">Courses</a></li>
      <li><a href="/users">Users</a></li>
    </ul>
  </nav>

  <main>
    <h2>Page Title Here</h2>
    <!-- THIS is where each page's unique content goes:
         tables for Read, forms for Create/Update, etc. -->
  </main>

  <footer>
    <p>&copy; 2026 College Manager</p>
  </footer>

</body>
</html>
```

Every future page is a copy of this with different stuff inside `<main>`.

[[extras\|next]]


