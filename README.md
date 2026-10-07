# iclone os — releases

Signed and notarized builds of **iclone os** for macOS (Apple silicon).

This repository holds release files only: the installer, the auto-update feed and the pinned agent runtime. It contains no source code.

## Install

1. Download `iclone-os-mac-arm64.dmg` from the [latest release](https://github.com/devclone20/iclone-os-releases/releases/latest).
2. Open it and drag **iclone os** into **Applications**.
3. Launch it from Applications.

Requires macOS on Apple silicon (M1 or later). Every build is signed with Developer ID (team `HJSLQL98D8`) and notarized by Apple.

## Verify a download

```bash
shasum -a 256 iclone-os-mac-arm64.dmg
```

Compare the result with `SHA256SUMS.txt` in the same release.

```bash
spctl -a -vvv -t open --context context:primary-signature iclone-os-mac-arm64.dmg
```

It should report `accepted` and `source=Notarized Developer ID`.

## Files in each release

| File | Purpose |
|---|---|
| `iclone-os-mac-arm64.dmg` | Installer |
| `iclone-os-<version>-mac-arm64.zip` + `.blockmap` | In-app updates |
| `latest-mac.yml` | Update feed read by the app |
| `runtime.json` | Pinned agent runtime commit and its source tarball hash |
| `SHA256SUMS.txt` | Checksums of all of the above |

## Credits

The agent runtime is [Hermes Agent](https://github.com/NousResearch/hermes-agent) by Nous Research (MIT). Third-party notices ship inside the app.
