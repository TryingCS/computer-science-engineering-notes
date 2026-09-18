---
{"dg-publish":true,"permalink":"/html-tags/","dg-note-properties":{}}
---

#html 

Tags wrap stuff or stand alone. Attributes are settings. Content can be text or nested elements.
***

Think of a **tag** as a **label you slap on something**.

### most tags

```html
<p>Welcome to the app</p>
```

Read it out loud like this:

> "**Paragraph start** → Welcome to the app → **Paragraph end**"

That's it. `<p>` = "a paragraph starts here". `</p>` = "the paragraph ends here". The text in the middle is the **content** — the stuff being wrapped.

The **whole thing** from `<p>` to `</p>` is called an **element**. So:

| Part | Name | Example |
|---|---|---|
| `<p>` | opening tag | |
| `Welcome to the app` | content | |
| `</p>` | closing tag | |
| all of it together | **element** | `<p>Welcome to the app</p>` |

The closing tag is just the opening tag with a `/`. That's the only rule.

```html
<h1>College Manager</h1>
<button>Save</button>
<a href="/login">Login</a>
```

Same pattern every time. Open → content → close.

---

### Tags with NO content (the "self-closing" ones)

Some tags don't wrap around anything. They just **exist at a spot**, like a wall switch. You don't put stuff "inside" a light switch.

```html
<input type="text">
<br>
<img src="logo.png">
```

- `<input>` → "put a text box here." There's no text *inside* it. It **is** the box.
- `<br>` → "line break here." Nothing goes inside a line break.
- `<img>` → "show an image here." The image isn't *inside* the tag; the tag just points to a file.

That's all "no content" means. **The tag does a thing at that spot instead of wrapping around words.**

You'll recognise them because they never have a closing version. You'll never see `</input>` or `</br>`.

---

### Attributes = settings you add to a tag

```html
<input type="text">
```

- `input` → the tag ("give me a box")
- `type` → the **attribute name** ("what kind of box?")
- `"text"` → the **value** ("a text kind")

Another one:

```html
<a href="/dashboard">Go to Dashboard</a>
```

- `a` → tag ("this is a link")
- `href` → attribute ("where does it go?")
- `"/dashboard"` → value ("to the dashboard page")
- `Go to Dashboard` → the visible text the user clicks

**Pattern:** `attribute="value"`. Always inside the opening tag. Always `name="value"` with quotes.

---

## "How many do I memorise?"

**Almost none.** Seriously.

There are ~110 HTML tags total. For your CRUD app you'll use maybe **15–20** repeatedly. And even those you won't memorise by drilling — you'll just type them so many times they stick, like how you don't "memorise" the word "the".



Your goal right now: understand the **pattern** (open → content → close, or just a single tag with settings). Once the pattern is in your hands, every new tag is just a new word following the same grammar.

---

Content = whatever sits between the opening and closing tag. Can be text, other elements, or both.
Is content always visible?
Mostly yes,

[[Layout\|next]]
