# idols Link — releases

Public release channel for **idols Link** and **idols Backend** installers.

Repository: [github.com/hqnatx/idols-link-release](https://github.com/hqnatx/idols-link-release)

## How auto-updates work

On startup (once per session), **idols Link** checks this repo's [GitHub Releases](https://github.com/hqnatx/idols-link-release/releases):

1. **idols Link** — compares the running launcher version with the newest release that includes a **Link** setup (`.exe` / `.msi` whose name contains `link` or `launcher`, not `backend`). If a newer version exists, it downloads the installer and runs it, then exits.
2. **idols Backend** (Windows, local backend mode) — if idols Backend is already installed, compares the executable's product version with the newest release that includes a **Backend** setup (name contains `backend`). If newer, it downloads and runs that installer.

Users can disable checks in **Settings → Appearance → Disable update checks**.

## Publishing a release

1. Build installers (examples):
   - `idols Link Setup-2.1.0.exe`
   - `idols Backend Setup-x.y.z.exe`
2. Open [Releases](https://github.com/hqnatx/idols-link-release/releases) → **Draft a new release**.
3. **Tag** = version users should receive, e.g. `v2.1.0` or `2.1.0` (must be **higher** than the previous tag for auto-update to trigger).
4. Attach both installers to the **same** release when you ship Link + Backend together, **or** create separate releases (newest matching asset per app is picked from the last 20 releases).
5. Optional: paste changelog in the release description (shown in manual "Update notes" in the launcher).

### Asset naming (important)

| App | Filename should include | Example |
|-----|-------------------------|---------|
| idols Link | `link` or `launcher`, plus `setup` / `installer` | `idols Link Setup-2.1.0.exe` |
| idols Backend | `backend`, plus `setup` / `installer` | `idols Backend Setup-1.0.0.exe` |

Avoid putting the word `backend` in the Link installer name, and avoid `link` in the Backend-only installer name.

## Source code

Application source and development builds live in the private/main repos (`idols-Link`, `idols-Backend`). **This repo is only for shipping binaries** to players.

## Notes

- Releases must be **published** (not draft) for the launcher to see them.
- Pre-releases are skipped unless no stable release has a matching installer.
- Rate limits: public API works without a token; for heavy CI use a `IDOLS_GITHUB_TOKEN` at build time if needed.
