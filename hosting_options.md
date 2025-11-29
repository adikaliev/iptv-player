# Hosting Options for IPTV Playlist Viewer


## GitHub Pages
- Supports static sites (HTML/CSS/JS) for free.
- Enable through Repository Settings > Pages, target the `master` branch root.
- Auto-builds on every push, served at `https://<user>.github.io/<repo>/` over HTTPS.
- Good for public code; private repos require paid plan.

## Netlify
- Connect GitHub repo or drag-and-drop the build folder.
- Free tier includes global CDN, HTTPS, deploy previews, and custom domain support.
- Works out of the box because no build step is required (deploy command can be `npm run build` or left blank).

## Vercel
- Designed for static and serverless apps; static deployment is as simple as linking the repo.
- Free tier includes SSL, CDN edge network, and preview deployments per pull request.
- Ideal if you later add tooling/build steps, though it�s equally fine for pure static content.

## Cloudflare Pages
- GitHub/GitLab integration, zero-cost plan with generous bandwidth.
- Builds the site in their edge network; static assets benefit from Cloudflare caching.
- Simple configuration: set build command to `null` and output directory to `/`.

## Other Free Hosts
- Surge.sh for CLI-based deployments (`surge . <subdomain>.surge.sh`).
- Render static sites and Firebase Hosting for small projects.

**Recommendation:** Start with GitHub Pages for tight Git integration and easy updates; add Netlify or Vercel if you want deploy previews, custom headers, or per-branch environments.
