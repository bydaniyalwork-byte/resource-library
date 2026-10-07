# Resource Library

An offline-first Android app for saving, organizing, finding, and backing up useful websites and digital tools.

## Run & Operate

- `pnpm --filter @workspace/resource-library run dev` — run the Expo mobile app
- `pnpm --filter @workspace/api-server run dev` — run the shared API server (not required by the app)
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- The mobile library stores resources, categories, and theme selection locally; no backend or sign-in is required.

## Stack

- pnpm workspaces, Node.js 24, TypeScript
- Mobile app: Expo + React Native + Expo Router
- Local persistence: AsyncStorage; site icons and backup files use device storage
- The API server provides a restricted website-metadata proxy for web previews; library data remains on-device.

## Where things live

- `artifacts/resource-library/app/` — mobile navigation and screens
- `artifacts/resource-library/context/LibraryContext.tsx` — offline library state and persistence
- `artifacts/resource-library/constants/themes.ts` — accent themes and app colors
- `artifacts/resource-library/lib/siteIcons.ts` — website metadata and locally cached logos

## Architecture decisions

- Saved data stays on-device by default; JSON import/export is the backup path.
- Deleting a category moves its resources to the permanent `Other` category instead of deleting them.

## Product

- Save and manage resources with a name, URL, description, category, favorite status, and website logo.
- Search instantly, browse by category, view favorites, and open a website directly.
- Create and manage categories, choose among ten color themes, and track collection counts.
- Export and restore a full JSON library backup.

## User preferences

_Populate as you build — explicit user instructions worth remembering across sessions._

## Gotchas

_Populate as you build — sharp edges, "always run X before Y" rules._

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
