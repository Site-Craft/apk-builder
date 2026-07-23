# apk-builder

This is the GitHub Actions builder repo used by the **HTML → APK Converter**.
Lovable pushes a `build/<uuid>` branch here for each build; the workflow reads
`build-config.json` + `www/**` and produces a debug-signed APK.

## One-time setup

1. Commit these two files to the `main` branch of this repo:
   - `.github/workflows/build.yml` (this repo)
   - `README.md` (this file)
2. Create a **Fine-grained Personal Access Token** with access to this repo and:
   - `Contents: Read and write`
   - `Actions: Read and write`
   - `Metadata: Read-only` (auto-selected)
3. In Lovable, this token is what the **GitHub connector** uses. Nothing else to do here.

## What each build produces

- Workflow run on branch `build/<uuid>`
- Artifact named `app-debug-apk` containing `app-debug.apk`
- Lovable downloads and serves that APK back to the user.

## Notes

- Debug-signed only. Not Play Store eligible.
- First build ~5 min (Gradle cold cache). Subsequent builds ~2–3 min with Actions cache.
- The Capacitor Android scaffold is generated fresh on every run — this repo stays lightweight.
