# Rebuild "Polarity Switcher" from GitHub

Migrate the public repository `anas810/toggle-flow-garden` into this Lovable project as a 1:1 rebuild of the existing site.

## What we're rebuilding

A single-page TanStack Start app called "Polarity Switcher" / "The Central Bank — Standard Reserve, Explained". It has a beige background, a custom font (Archivo + IBM Plex Mono), and a toggle that switches between "expansion" (positive net capital flow, green particles flowing into a central bank) and "contraction" (negative flow, red particles flowing out). The page updates copy, issuance rate, fee routing, and reserve status to match the selected state.

## Source inspection summary

- Stack: TanStack Start, React 19, Tailwind CSS v4, shadcn/ui primitives.
- No backend, auth, external APIs, or database.
- No record export needed.
- Google Fonts loaded via `<link>` in `__root.tsx`.

## Files to change

1. `src/styles.css` — replace with the source theme (beige palette, `--paper`, `--ink`, `--hairline`, `--expansion`, `--contraction`, Archivo/IBM Plex Mono fonts, fade-in animation).
2. `src/routes/__root.tsx` — add Google Fonts preconnect and stylesheet links; keep the existing root layout/error/404 shell.
3. `src/routes/index.tsx` — replace the placeholder with the full polarity-switcher landing page (head metadata, state toggle, copy panels).
4. `src/components/BankCanvas.tsx` — create the canvas particle animation and central bank drawing.
5. `src/components/IssuanceRate.tsx` — create the issuance-rate sparkline + "+1" token animation.
6. `src/components/FeeRouting.tsx` — create the fee-routing vault/furnace animation.

## Files to leave unchanged

- `package.json` and dependencies (already identical to source).
- Existing shadcn/ui components under `src/components/ui/`.
- Router, server entry, config, tooling (`src/router.tsx`, `src/server.ts`, `src/start.ts`, `vite.config.ts`, etc.).

## Verification

- Run `vite build` (or let the harness typecheck/build) to confirm no import or type errors.
- Open the preview and confirm: beige background, toggle switches positive/negative, particles change direction and color, all text updates, and no console errors.
