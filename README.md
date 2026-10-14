# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## GitHub Pages deployment

In **Settings → Pages**, set the source to **GitHub Actions**. The Pages workflow
builds the app with Node.js 22 and deploys `dist` on pushes to `master` (or a manual
workflow run). The site is hosted at
https://skilledminds.github.io/quantumpod-light/.

Vite's base path and the router basename use `/quantumpod-light/`. The workflow
copies the built HTML into entry pages for `/careers`, `/it-outsourcing`, and
`/admin/jobs` so direct visits and refreshes work without SPA rewrites. Add an
entry page to the workflow when adding a route.

For job listings and administration, configure repository or `github-pages`
environment secrets named `VITE_SUPABASE_URL` and `VITE_SUPABASE_ANON_KEY`.
These are injected at build time; rerun the deployment after changing them.
For local development, set the same variables in an ignored `.env` file.
Without both values, the public site still renders and the careers/admin pages
display an unavailable message.

Vite embeds these values in public JavaScript. Use only the Supabase public anon
key, **never a service-role key**, and enforce access with Supabase Row Level
Security policies. The current client-side admin password is not server-side
authorization; database policies must independently protect job mutations.

To check the build locally, run `npm ci`, `npm run build`, and `npm run preview`,
then visit http://localhost:4173/quantumpod-light/.
