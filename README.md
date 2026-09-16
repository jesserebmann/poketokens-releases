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

## Installing on Windows

The Windows bundle is tracked in this repository at a fixed path, so the link
never changes between versions:

    https://github.com/jesserebmann/poketokens-releases/raw/main/windows/PokeTokens-windows.zip

`windows/VERSION` says which version that file is. It needs the .NET 9 Desktop
Runtime (`winget install Microsoft.DotNet.DesktopRuntime.9`) and nothing else —
the Swift and MSVC runtimes travel inside the zip.

```powershell
$zip = "$env:TEMP\PokeTokens-windows.zip"
$dest = "$env:LOCALAPPDATA\Programs\PokeTokens"
Invoke-WebRequest -Uri "https://github.com/jesserebmann/poketokens-releases/raw/main/windows/PokeTokens-windows.zip" -OutFile $zip
Get-Process PokeTokens -ErrorAction SilentlyContinue | Stop-Process
Expand-Archive -Path $zip -DestinationPath $dest -Force
& "$dest\PokeTokens.exe"
```

The same command updates an existing install and leaves your save in
`%LOCALAPPDATA%\PokeTokenBar` untouched.
