# minimap-dist

Distribution channel for the **minimap** desktop app — its release binaries and the update manifest.
Separate from the plugin registry (`mapcrate/plugin-registry`): that catalogs *plugins*, this ships
the *app*.

- **`app.json`** — the latest app release the running app checks for self-update:
  ```json
  { "version": "0.2.3", "url": "…/releases/download/v0.2.3/minimap.exe", "notes": "…" }
  ```
  The app fetches this at startup; if `version` is newer than what's running, it offers an in-app update.
- **Releases** — each app version is a GitHub release here (tag `v<version>`) with `minimap.exe` attached.

## Publishing a new app version
1. Build the single-file `minimap.exe`.
2. `gh release create v<version> minimap.exe -R mapcrate/minimap-dist -t "minimap <version>"`
3. Bump `app.json` (`version`, `url`, `notes`) and commit.
