# Hacktoolkit Chrome extensions: notes for AI agents and contributors

This repository is only a collection. Each extension is a git submodule with its own repository, README, Makefile and (where present) AGENTS.md. **All work happens inside the submodule**, on a branch of that repository, with a pull request there. Bump the submodule pointer here after the extension's PR merges.

| Extension | Manifest | Notes |
| --- | --- | --- |
| organize-tabs-chrome-extension | V3 | Reference implementation: service-worker architecture, unit tests, e2e, holodeck, demo recorder. The skeleton is distilled from it. |
| github-jira-chrome-extension | V3 | |
| paywall-xray-chrome-extension | V3 | |
| notes-chrome-extension | V2 | Manifest V2 no longer loads in current Chrome; needs a V3 migration. |

## Starting a new extension

Use the template repository [hacktoolkit/htk-chrome-extension-skeleton](https://github.com/hacktoolkit/htk-chrome-extension-skeleton): **Use this template** on GitHub, then run `node scripts/init.mjs "Name" "Description" hacktoolkit/<repo>` once. It ships as a small working extension with the service-worker architecture, a pure tested logic module, the action registry, settings sync, the holodeck scripts, a headless e2e suite and CI already wired. Add the new repository here as a submodule.

## Conventions

- Vanilla JavaScript, no build step, no runtime dependencies. ES modules are fine (`"type": "module"` on the service worker).
- Every project has a Makefile with `help`, `test`, `package`, and where a browser is involved, `dev`, `e2e` and `dev-clean`.
- Pure logic goes in a `lib/` module with a `node --test` suite; Chrome API calls stay in a thin layer around it.
- Code style per `.prettierrc`: 4 spaces, single quotes, semicolons.

## The holodeck

Browser testing never touches a real profile. Automated and interactive runs use the **holodeck**, a throwaway sandbox at `~/.holodeck/` (override with `HOLODECK=`):

- `make dev` opens Brave (or `BROWSER=/path/to/chromium make dev`) on a persistent profile at `~/.holodeck/<browser>/`, named "🧪 holodeck" in the profile chip, with the extension loaded unpacked and sample tabs seeded.
- `make e2e` uses a fresh profile under `~/.holodeck/tmp/`, deleted when the run ends.
- `make dev-clean` deletes the holodeck profiles.
- Google Chrome's branded build ignores `--load-extension`; the scripts default to Brave. Loading unpacked through `chrome://extensions` works in any browser.

Agents may create, inspect and destroy anything under `~/.holodeck/` without asking. See `organize-tabs-chrome-extension/scripts/dev.mjs` and `scripts/e2e.mjs` for the reference implementation.
