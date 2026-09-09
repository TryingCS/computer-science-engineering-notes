---
{"dg-publish":true,"permalink":"/assets/subjects/z-misc/github-pages/","dg-note-properties":{}}
---

#misc 
GitHub Pages can host a React frontend **if it builds to static files**. #hosting

Typical setup:

```bash
npm run build
```

Then deploy the `build/` or `dist/` folder to GitHub Pages.

Important notes:

- For **Vite**, set:

```js
base: "/your-repo-name/"
```

- For **Create React App**, set in `package.json`:

```json
"homepage": "https://your-username.github.io/your-repo-name/"
```

- If using **React Router**, GitHub Pages does not natively support SPA routing. You need a workaround like redirecting to `index.html`, often using a `404.html` copy or a GitHub Action.

Simple deployment options:

1. **GitHub Actions**
2. **`gh-pages` npm package**
3. Deploy the build folder manually to a `gh-pages` branch

Example with `gh-pages`:

```bash
npm install --save-dev gh-pages
```

Add to `package.json`:

```json
"scripts": {
  "deploy": "npm run build && gh-pages -d build"
}
```

Then run:

```bash
npm run deploy
```

For Vite, use `dist` instead:

```bash
gh-pages -d dist
```

***
