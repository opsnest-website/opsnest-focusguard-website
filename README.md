# FocusGuard website

Public home of **FocusGuard**, the OpsNest Android app for screen-time limits.

- **Website:** <https://opsnest.in/focusguard/>
- **Privacy policy:** <https://opsnest.in/focusguard/privacy/> (the URL used for Google Play)
- **Downloads:** [Releases](https://github.com/opsnest-website/opsnest-focusguard-website/releases)

The app's source code is in a private repository. Its release workflow publishes every signed
build (APK and release notes) to this repository's **Releases**, and the app's opt-in update check
reads them from here. APKs are attached to releases, not committed to the repository.

## Layout

```
site/                 static site, no build step
  index.html          landing page
  privacy/index.html  privacy policy
  styles.css
  assets/icon.svg
```

Links inside `site/` are relative, so the site works wherever it's served from.

## How it's published

This repository is a Git submodule of [OpsNest](https://github.com/opsnest-website/OpsNest) at
`modules/focusguard`. The OpsNest Pages workflow copies `site/` to `/focusguard/` on
`opsnest.in`. A change here goes live once OpsNest pins the new commit (Dependabot opens that PR).

Preview locally:

```bash
python3 -m http.server -d site 8000   # http://localhost:8000
```

## Updating the privacy policy

Edit `site/privacy/index.html` and change the **Effective date**. Keep it in step with the app: any
new permission, network call or data shared must be described there before it ships.
