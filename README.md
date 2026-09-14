# PokeTokenBar — releases

Download the latest build from [Releases](../../releases).

This repository holds **release artifacts only** — no source. The source lives
in a private repository, so this exists purely so the app's update check has
somewhere public to read from: GitHub's releases API answers `404` for a private
repository to an unauthenticated caller, and the alternative would have been
shipping a GitHub token inside the app.

## Installing

1. Download `PokeTokenBar.zip` from the latest release.
2. Unzip it and move `PokeTokenBar.app` to your Applications folder.
3. On first launch, right-click the app and choose **Open** — the build is
   signed with a self-signed certificate, so Gatekeeper asks once.

Updating later is the same steps; the app tells you when a new version is out.
