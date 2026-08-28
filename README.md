# Macopy — releases

Public downloads for [Macopy](https://macbuff.com/apps/macopy), a clipboard manager for macOS.

**The source lives in a separate private repository.** This repo exists only so
customers can download the app and so the in-app update check has something to
read — GitHub serves raw files and release assets anonymously from public repos
only, and a customer must never need a GitHub account to get an update.

## Download

Get the latest DMG from [Releases](../../releases/latest).

Requires macOS 13 or later. Universal — Apple Silicon and Intel.

## What `latest.json` is

MacBuff apps fetch this file at most once a day and tells you when a newer version
exists. It never installs anything on its own.

```json
{ "version": "2.2", "url": "https://…/Macopy.dmg", "notes": "…" }
```

Publishing a new version:

1. `./build-dmg.sh` in the private repo (signs, notarizes and staples)
2. Upload `Macopy.dmg` to a new GitHub Release here, tagged `v<version>`
3. Bump `version`, and write `notes` as a sentence a customer would want to read
4. Commit — the `url` above always resolves to the newest release, so it never
   needs changing

Keep `version` matching `APP_VERSION` in `config.sh` exactly. If this file
claims a version that no release provides, every customer gets an update prompt
that leads nowhere.

## Support

Something broken? Email the address in the app under **Settings → Help**.
