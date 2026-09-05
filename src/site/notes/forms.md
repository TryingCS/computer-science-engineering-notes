---
{"dg-publish":true,"permalink":"/forms/","dg-note-properties":{}}
---


#html 

Everything the user **types, selects, or submits** is a form. 


## The `<form>` wrapper

Every form starts with:

```html
<form action="/students" method="POST">
  <!-- inputs go here -->
</form>
```

| Attribute | What it does |
|---|---|
| `action="/students"` | **Where** the data gets sent (a URL on your server). |
| `method="POST"` | **How** it's sent. `POST` for creating/updating data. `GET` for search/filter queries. |

> ⚠️ **Heads-up:** `action` and `method` only matter once you have a **backend** to receive the data. In pure HTML with no server, clicking submit does nothing useful. 

---

## `<input>` — the workhorse

`<input>` is self-closing (no content). You control what it does via the `type` attribute.

### The types you'll use constantly:

```html
<input type="text" name="username">
<input type="email" name="email">
<input type="password" name="password">
<input type="number" name="age">
<input type="date" name="enrollment_date">
<input type="hidden" name="student_id" value="42">
```

| `type` | What it gives you | CRUD use |
|---|---|---|
| `text` | Single-line text box | Name, title |
| `email` | Text box that validates email format | Email field |
| `password` | Text box that hides characters (dots) | Login, register |
| `number` | Numeric input with arrows | Age, credits, capacity |
| `date` | Date picker | Enrollment date, DOB |
| `hidden` | Invisible to user, still submits a value | IDs, tokens (Edit/Delete) |

### The `name` attribute — critical

```html
<input type="text" name="first_name">
```

`name` is the **key** sent to your server. If the user types "Ahmed", your backend receives `first_name=Ahmed`. **Every input that must send data needs a `name`.** No `name` = data is ignored on submit.

### `value` — pre-filling

```html
<input type="text" name="first_name" value="Ahmed">
```

The box shows "Ahmed" already. You'll use this for **Edit/Update** forms: load existing data into the fields.

### `placeholder` — hint text

```html
<input type="email" name="email" placeholder="you@college.edu">
```

Grey hint text that disappears when the user clicks. It's **not** a value. It doesn't get submitted.

---

## `<label>` — always pair it with your input

```html
<label for="email">Email Address</label>
<input type="email" id="email" name="email">
```

- `for="email"` on the label matches `id="email"` on the input.
- Clicking the label **focuses** the input. Accessibility win.
- Screen readers announce the label when the input is focused.

**Rule:** every visible input gets a `<label>`. No exceptions.

You can also wrap the input inside the label (no `for`/`id` needed):

```html
<label>
  Email Address
  <input type="email" name="email">
</label>
```

Both approaches work. Pick one style and be consistent.

---

## `<button>` — submitting and other actions

```html
<button type="submit">Save Student</button>
<button type="reset">Clear Form</button>
<button type="button">Do Something (JS handles this)</button>
```

| `type` | Behaviour |
|---|---|
| `submit` | Sends the form to the `action` URL. **Default if you omit type.** |
| `reset` | Clears all fields back to defaults. |
| `button` | Does nothing on its own. You wire it up with JS. |

> ⚠️ **Heads-up:** `type="button"` is useless without **JavaScript** to listen for clicks. You'll use it for things like "Cancel", "Delete" (with a JS confirmation), or dynamic UI actions.

---

## Your first real form: Login

```html
<main>
  <h2>Login</h2>

  <form action="/login" method="POST">

    <label for="email">Email</label>
    <input type="email" id="email" name="email" required>

    <label for="password">Password</label>
    <input type="password" id="password" name="password" required>

    <button type="submit">Login</button>

  </form>
</main>
```

`required` is a **built-in validation attribute**. The browser won't submit if the field is empty. No JS needed.

---

## A "Create Student" form

```html
<main>
  <h2>Add New Student</h2>

  <form action="/students" method="POST">

    <label for="fname">First Name</label>
    <input type="text" id="fname" name="first_name" required>

    <label for="lname">Last Name</label>
    <input type="text" id="lname" name="last_name" required>

    <label for="email">Email</label>
    <input type="email" id="email" name="email" required>

    <label for="dob">Date of Birth</label>
    <input type="date" id="dob" name="dob">

    <label for="gpa">GPA</label>
    <input type="number" id="gpa" name="gpa" min="0" max="4" step="0.01">

    <button type="submit">Add Student</button>
    <button type="reset">Clear</button>

  </form>
</main>
```

Notice `min`, `max`, `step` on the number input. Built-in validation. Browser enforces them.
