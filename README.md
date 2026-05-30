# idols Link — releases

Public release channel for **idols Link** Windows installers.

Repository: [github.com/hqnatx/idols-link-release](https://github.com/hqnatx/idols-link-release)

**idols Backend** installers are published separately: [idols-Backend-release](https://github.com/hqnatx/idols-Backend-release).

## How auto-updates work

On startup (once per session), **idols Link** checks this repo's [GitHub Releases](https://github.com/hqnatx/idols-link-release/releases):

- Compares the running launcher version with the newest release that includes a **Link** setup (filename contains `link` or `launcher`, not `backend`).
- If newer, downloads the installer, runs it, and exits.

Backend auto-updates use [idols-Backend-release](https://github.com/hqnatx/idols-Backend-release).

Users can disable checks in **Settings → Appearance → Disable update checks**.

## Publishing a release

1. Build the launcher installer, e.g. `idols Link Setup-2.1.0.exe`.
2. Open [Releases](https://github.com/hqnatx/idols-link-release/releases) → **Draft a new release**.
3. **Tag** = version to ship, e.g. `v2.1.0` (must be **higher** than the previous tag).
4. Attach the setup `.exe` or `.msi`.
5. Optional: changelog in the release description (manual "Update notes" in the launcher).

### Asset naming

| Include in filename | Example |
|---------------------|---------|
| `link` or `launcher`, plus `setup` / `installer` | `idols Link Setup-2.1.0.exe` |

Do **not** put `backend` in the Link installer name.

## Source code

Application source lives in `idols-Link`. **This repo is only for shipping binaries** to players.

## Notes

- Releases must be **published** (not draft).
- Pre-releases are skipped unless no stable release has a matching installer.
