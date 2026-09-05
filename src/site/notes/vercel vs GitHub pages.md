---
{"dg-publish":true,"permalink":"/vercel-vs-git-hub-pages/","dg-note-properties":{}}
---


#dev
when to use vercel instead: ( even if the output is static) :
 ==when the *build* isn't trivial==
- eg: raw markdown plus a Node build pipeline: Eleventy, Sass, image optimization (sharp), search index, favicon generation. 
- 
- Something has to run `npm install && npm run build` on every push.
- **Vercel does that natively for free**: push → build → CDN, plus per-PR preview deployments and one-click rollbacks 
- **GitHub Pages natively only builds Jekyll** (Ruby).
- 
- To run a Node build on Pages => GitHub Actions
 Vercel = free CI/CD that speaks Node