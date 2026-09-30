# empty-vite-vue-electron-ts-pinia-template

A starter template for a desktop app built with Vue 3, Vite, TypeScript, Pinia and Electron.

## Attribution

This repository is a **starter template, not original work**. It is based on
[Yukun-Guo/vite-vue3-electron-ts-template](https://github.com/Yukun-Guo/vite-vue3-electron-ts-template)
(MIT, Copyright (c) 2022 Yukun Guo). The Electron/Vite setup, scripts and most of the git history
(29 of 32 commits) are by Yukun. The only changes here (Feb 2025) strip the demo content
(example components, images, README) to leave an empty skeleton.

## Tech stack

Versions as declared in `package.json`:

- Vue 3 (`^3.2.25`), Vue Router 4, Pinia 2
- Vite 2 with `@vitejs/plugin-vue`
- TypeScript 4.5, `vue-tsc`
- Electron 25, packaged with electron-builder 24 (NSIS on Windows, DMG on macOS)

## Setup

Requires Node.js and npm.

```sh
npm install
```

## Scripts

| Script | What it does |
| --- | --- |
| `npm run vite:dev` | Vite dev server (renderer only) |
| `npm run vite:build` | Type-check with `vue-tsc`, then build the renderer |
| `npm run vite:preview` | Preview the Vite build |
| `npm run ts` / `npm run watch` | Compile (or watch) the Electron main/preload code to `dist/electron` |
| `npm run app:dev` | Compile, then run Vite, Electron and `tsc -w` together |
| `npm run app:build` | Build renderer, compile Electron code, package with electron-builder (output in `release/`) |
| `npm run app:preview` | Build, then start with Electron |
| `npm run lint` | ESLint (no ESLint config is committed, see Status) |

## Project structure

```
src/
  electron/main/main.ts        Electron main process (creates an 800x600 window)
  electron/preload/preload.ts  Preload script (exposes an openFile IPC bridge)
  main.ts                      Vue entry: mounts the app with Pinia and Vue Router
  App.vue                      Empty root component
  router/index.ts              Route definitions
  store/counter.ts             Pinia store stub
  views/, components/          Empty placeholder components
```

## Status

Empty skeleton, not a working app out of the box. Observed from the code (not from running it):

- `src/router/index.ts` imports `../components/Home.vue` and `../components/About.vue`, which do not exist, so the renderer build will fail until they are added or the routes are changed.
- `src/electron/main/main.ts` does not register the `dialog:openFile` handler that the preload script invokes.
- `npm run lint` references `.eslintrc`, which is not in the repo; `package.json` still has placeholder `author` and `appId` values.
- Dependencies are old (Vite 2, Electron 25) and have not been updated.

## Screenshots

_Placeholder: none yet._

## License

The upstream project is MIT-licensed by Yukun Guo, but this repository currently has no `LICENSE` file (the upstream one was removed in an earlier commit). Restoring it is an open decision for the repository owner.
