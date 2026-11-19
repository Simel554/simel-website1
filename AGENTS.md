# Project notes

freecode reads this file before every change. Add anything it should always remember about this project.

## This project
- React 19 + TS + Vite (Vite+ `vp` tooling in this workspace), framer-motion + Lenis, fonts via @fontsource.
- All personal copy/projects/links live in `src/data/site.ts`. Visual system is in `DESIGN.md`.
- `albert-simel-portfolio.zip` is the downloadable plain-Vite export of the same site (npm, `vite`/`@vitejs/plugin-react`, `vercel.json`). Regenerate it if source changes.
- `/tmp/makezip.sh` style workflow: source uses `vp`; the export must switch scripts to plain `vite` and `tsc`.
