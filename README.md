# Vault: encrypted, portable photo & file vaults for Android

An Android app for keeping private photos, videos and documents in encrypted vaults that belong to you, not to a cloud provider.

Vault runs on **[Aqua](https://github.com/hamzaasgharkhan/FileSystem)**, a filesystem I wrote from scratch in Java. It encrypts everything (contents, file names and folder structure) with AES-256-GCM, using a key derived from your password. A vault is a self-contained folder that can be opened by any device running the library. No account or internet connection is needed.

## Features

- Create multiple password-protected vaults and mount or unmount them
- Import photos, videos and other files from the device
- Browse folders in a list or a thumbnail grid (thumbnails are stored encrypted, so the gallery loads without decrypting full-size files)
- Open files in the system viewer
- Create, rename, move, copy and delete files and folders, including multi-select
- Export a whole vault to `Documents/Vault/` so it can be copied to another device and opened there
- Export individual files back out, decrypted, to the device's Documents or DCIM folder

## Tech

- **Kotlin**, **Jetpack Compose** (Material 3), Navigation Compose
- **MVVM**: an `AppViewModel` holds UI state (`StateFlow`) and calls into the filesystem
- The Aqua filesystem library (`app/libs/filesystem.jar`) with Bouncy Castle and Thumbnailator
- minSdk 30, targetSdk 34

## Building

Open in Android Studio and run the `app` configuration, or:

```bash
./gradlew assembleDebug
```

## How it fits together

```
Compose UI  ──►  AppViewModel  ──►  Aqua FileSystem (Java)  ──►  encrypted store files on disk
```

See the [FileSystem README](https://github.com/hamzaasgharkhan/FileSystem) for the on-disk format and encryption design.
