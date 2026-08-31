# Repository guidelines for AI agents

These instructions apply to all AI agents (including Cursor Cloud Agents) working in this repository.

## Communication

- Write every explanatory response directed at the user in **Italian** — this includes summaries, status updates, explanations, questions, and final answers. Keep code, code comments, commit messages, branch names, identifiers, file paths, and pull request titles/descriptions in their existing language (typically English) unless the user asks otherwise.

## Development environment

- The project is a Cloudflare Worker. Use the canonical commands: `npm run typecheck`, `npm run test`, and `npx wrangler deploy --dry-run` (build check). CI (`.github/workflows/ci.yml`) runs these plus the installer worker bundle (`cd installer && npm run bundle-worker`).
- The `AI` binding is remote-only and `Vectorize` has no local emulation, so run the dev server with `npx wrangler dev --local` (no Cloudflare credentials needed). In this mode semantic capture/recall are unavailable by design; those paths are covered by the `vitest` suite with mocked bindings.
