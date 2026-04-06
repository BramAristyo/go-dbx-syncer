# Dropbox Image Synchronization (Internal Use - Nayati)

A specialized Go-based tool designed for internal use at **Nayati** to efficiently synchronize files from a specific Dropbox directory to a local storage path. This script ensures that local copies are always up-to-date by comparing modification times and file names, downloading only new or updated assets.

## Purpose & 
This tool was developed to solve a specific synchronization challenge within our workflow. 

> **Detail on the Problem Real:**
> [https://www.linkedin.com/posts/bram-aristyo_itsupportlife-golang-automation-activity-7440765238884327424-OhjK/]

---

## Features
- **Incremental Sync:** Only downloads files that are new or have been modified since the last sync.
- **Automated Authentication:** Uses Dropbox OAuth2 Refresh Tokens to automatically generate fresh Access Tokens, ensuring long-running stability without manual intervention.
- **Local Time Preservation:** Adjusts local file modification times to match Dropbox metadata for accurate future comparisons.
- **Jakarta Timezone Logging:** All operations are timestamped using the `Asia/Jakarta` timezone.

## Prerequisites
- Go 1.18 or higher.
- A Dropbox App registered via the [Dropbox Developers Console](https://www.dropbox.com/developers/apps).
- A valid Refresh Token with `files.metadata.read` and `files.content.read` permissions.

## Configuration
Create a `.env` file in the root directory based on the `.env.example`:

```env
DROPBOX_APP_KEY=your_app_key
DROPBOX_APP_SECRET=your_app_secret
DROPBOX_REFRESH_TOKEN=your_refresh_token
DROPBOX_PATH=/path/to/dropbox/folder

LOCAL_PATH=C:/path/to/local/folder
```

## Project Structure
- `cmd/app/`: Application entry point.
- `internal/config/`: Configuration and environment variable management.
- `internal/dropbox/`: Core logic for Dropbox API interaction (Auth, Download, Sync).
- `models/`: Data structures for tokens and file metadata.

---
**Internal Use Only** - Developed for Nayati Indonesia IT Server sync purposes.
