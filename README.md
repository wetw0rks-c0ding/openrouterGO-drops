# OpenRouter GO — drops

Releases of **OpenRouter GO**, an account manager for an
[OpenRouter](https://openrouter.ai) account, driven by a management key.
Android and iOS from one codebase.

The source is private: `wetw0rks-c0ding/openrouterGO`. This repository is the
**distribution point** — the files, and the manifest the app reads to know
whether there is something newer.

## Downloads

Every release has two files.

| file | what it is |
|---|---|
| `OpenRouterGO-<version>-android.apk` | The Android app. Signed with the house release key, so it installs over the previous release. |
| `OpenRouterGO-<version>-ios.ipa` | The iOS app. **Unsigned**, and built on Linux for **TrollStore** on a jailbroken device. It is not an App Store build, and `ideviceinstaller` will refuse it. |

## The manifest

[`latest.json`](latest.json) is what the app fetches to find out whether there
is a newer version:

```json
{
  "version": "1.0.0",
  "releasePageUrl": "https://github.com/wetw0rks-c0ding/openrouterGO-drops/releases/latest",
  "playStoreUrl": null
}
```

- `version` — the version currently published here.
- `releasePageUrl` — the page the app opens when it finds a newer version.
- `playStoreUrl` — reserved. `null` until the app is on the Play Store; when
  it is set, the app offers that as well as the release page.

The app **never claims to know the latest version unless a check succeeded.**
If it cannot read this file it says so, and says nothing about what the
latest version is.

## Installing the iOS build

The `.ipa` is unsigned. On a jailbroken device, open it in TrollStore, or
serve it and open it from the device. It installs, and the app's own
settings tell you what it can and cannot promise on iOS.
