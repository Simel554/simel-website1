# ~/albert simel — portfolio

Design system and motion language live in [DESIGN.md](./DESIGN.md).

React 19 + TypeScript + Vite, animated with framer-motion, inertia scrolling with Lenis,
fonts bundled locally (Syne + JetBrains Mono) so there is no Google Fonts request.

## Develop

```sh
npm install
npm run dev        # http://localhost:3000
npm run typecheck
npm run build      # static output in dist/
npm run preview    # serve the built dist/
```

## Deploy to Vercel (keeping simel-coral.vercel.app)

The site is fully static — no server, database, or environment variables.

Vercel detects Vite automatically; `vercel.json` pins build `npm run build` and output `dist/`.

- **Project linked to a Git repo:** replace the files in that repo with this folder, commit,
  push. The existing project builds and redeploys to the same address.
- **CLI:** in this folder run `npx vercel link` and pick the existing `simel-coral` project,
  then `npx vercel --prod`.

## Structure

- `src/data/site.ts` — all personal copy, projects, skills, links (edit content here)
- `src/components/` — Cursor, Nav, Hero, WorkIndex, ProjectDrawer, About, Contact, Marquee
- `src/styles/` — base, chrome, hero, work, about, contact
- `src/lib/` — motion tokens, smooth scroll
