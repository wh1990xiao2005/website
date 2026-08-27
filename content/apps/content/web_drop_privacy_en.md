---
title: "Privacy Policy"
---

**Last Updated: July 7, 2026**

## Introduction

WebDrop (the "App") is provided by an individual developer (referred to as "we") and offers **local network file sharing**. The App starts a local HTTP server on your device so that any browser on the same Wi-Fi network can browse, upload or download files in the directory you select. All transfers happen directly between your device and other devices on the local network — no data passes through any remote server.

We take your privacy seriously and will provide security safeguards for your personal information in accordance with applicable laws and well-established industry standards.

## Changes to This Notice

To make this notice clearer and more accurately describe how we handle information, we have updated the structure and wording as follows:

- Reorganized sections to follow a standard privacy policy template;
- Added descriptions for the optional "password protection" and "read-only mode" features;
- Refreshed the Android permissions list to match the manifest in the shipped build;
- Clearly stated that the App **does not collect, store, or transmit personal information to external servers**.

## Summary

- WebDrop is an offline, local-network file sharing tool. **It does not collect any personal information.**
- All files stay on your device — they are never uploaded to the cloud or to any third party.
- Permissions are requested only for the core functionality described in "Device Permissions".
- You can revoke any granted permission at any time via your system settings.

## 1. How We Collect and Use Your Information

We only process information related to personal details when there is a lawful basis for doing so. Because WebDrop runs **entirely on-device**, we do not collect, transmit, or sell any personal information to any external server.

### 1.1 Information We Process to Provide the Service

To deliver its core functionality, the App processes the following information **locally on your device**, and only when you actively enable the corresponding feature:

1. **File metadata** (file name, size, last modified time) — used solely to display the file list on the web UI for other devices to browse and download;
2. **Local network information** (Wi-Fi SSID, local IPv4 address) — used to display the access URL and generate the QR code on screen; never uploaded;
3. **App settings** — including shared directory, server port, password-protection enabled flag, read-only mode flag, keep-screen-on flag, etc., all stored locally in Android `SharedPreferences`;
4. **Bearer tokens** — only when you enable password protection. Tokens are valid for up to 12 hours, held in memory, used to authorize API calls, and **never sent off-device**;
5. **Transfer statistics** (upload/download byte counts, 1-second rolling speed) — kept in memory and shown only inside the App for the current session; **never sent off-device**.

Files you share *into* WebDrop from another app are written into the shared directory you selected. Such content stays on your device and is never transmitted to us or to any third party.

### 1.2 Personalized Recommendations

**Not applicable.** The App does not provide personalized content recommendations, advertising, or user profiling of any kind.

## 2. Device Permissions

The App may need the following permissions while running. We will request them before use, and no permission is invoked without your explicit consent:

- **Internet access** (`INTERNET`) — required to create the local HTTP server for file sharing on the LAN;
- **Network state access** (`ACCESS_NETWORK_STATE`) — used to detect Wi-Fi connectivity and stop the server automatically when Wi-Fi drops;
- **Change network state** (`CHANGE_NETWORK_STATE` / `CHANGE_WIFI_STATE` / `ACCESS_WIFI_STATE`) — used to read the current Wi-Fi SSID and monitor connectivity changes;
- **Wake lock** (`WAKE_LOCK`) — optional, only used when you enable "Keep Screen On" to prevent the screen from sleeping during sharing;
- **Foreground service** (`FOREGROUND_SERVICE`) — used to keep the local service alive during an active sharing session so that the system does not reclaim it under memory pressure;
- **Media / file access** — required to read and write files in the directory you choose. On Android 11+ this is handled through Scoped Storage; on lower versions the legacy `READ_EXTERNAL_STORAGE` / `WRITE_EXTERNAL_STORAGE` permissions are requested.

You can manage these permissions any time from *System Settings → Apps → WebDrop → Permissions*. Permission names may differ across OS versions or OEM skins; the actual dialogs on your device are authoritative.

## 3. Protection of Minors

We attach great importance to the protection of minors' personal information and will provide services strictly in accordance with applicable laws. If you are a minor, you must have your parent or legal guardian's consent to use the App and to accept the related terms. Parents or guardians should also take appropriate precautions — including supervising the minor's use of the App.

In particular, if you are a child under 14, please notify and read this notice together with your parent or legal guardian before using the App.

## 4. Sharing With Third Parties

**Not applicable.** The App is a fully local tool. There is no scenario in which your personal information is shared with any third party. All files and settings remain on your device and are never collected by us or by any third party.

## 5. Third-Party SDKs

To implement the App's core functionality, we integrate several **open-source** Flutter plugins and Android libraries. All of them work locally on your device and do not transmit personal information to any third-party server:

- **shelf / shelf_router** — local HTTP server;
- **network_info_plus** / **connectivity_plus** — local network status;
- **shared_preferences** / **path_provider** — local preference and path storage;
- **wakelock_plus** — keep-screen-on control;
- **qr_flutter** — render the QR code locally;
- **webview_flutter** — render bundled privacy / release-notes HTML inside the App;
- **open_file** / **package_info_plus** / **flutter_foreground_task** — file opening, version info, and foreground service.

The App does not contain any analytics SDK, push SDK, or ad SDK that collects personal information.

## 6. How We Protect Your Information

1. **Local-network boundary** — the HTTP server binds to your device's LAN IPv4 address (via `InternetAddress.anyIPv4`) and is reachable only on your Wi-Fi network; it is not exposed to the public internet.
2. **Path-traversal protection** — every file HTTP handler validates names through `FileUtils.isValidFilename` and rejects `..`, `/`, and `\`.
3. **Optional access control** — enable Bearer-Token auth in *Settings → Password Protection*; tokens expire 12 hours after issuance.
4. **Optional read-only mode** — *Settings → Read-Only Mode* blocks every write operation (upload, rename, delete, mkdir, move) while listing and download remain available.
5. **No persistent sensitive data** — the App does not log file contents, does not persist request logs, and does not upload crash reports.
6. **Data minimization** — settings live on your device only for as long as needed to deliver the functionality above.

> **Notice**: the App uses plain HTTP on the LAN. Please only enable sharing on trusted Wi-Fi networks and consider turning on password protection and read-only mode.

## 7. Managing Your Information

Because **no personal information is stored on any cloud backend**, most cases do not require active management. Nevertheless, you retain the rights described below:

### 7.1 Access

From within the App's *Settings* screen you can always view your device's IPv4 address, the shared directory path, server port, password-protection status, read-only status, and current upload/download speeds.

### 7.2 Correction

You can update the shared directory, port, password, and other preferences at any time from the App's *Settings*. All of these are stored locally on your device.

### 7.3 Deletion

You can delete information stored by the App at any time by:

- Using *Settings → Storage Cleanup* to clear the files inside a chosen directory;
- Manually deleting any file you no longer want to share from inside the App;
- Uninstalling the App to wipe all local data.

### 7.4 Withdraw Consent

If you no longer want the App to use a specific permission, you can revoke it from *System Settings → Apps → WebDrop → Permissions*. After revoking a permission, the related core features may become unavailable.

### 7.5 Account Cancellation

**Not applicable.** The App has no account system. Stopping the server or uninstalling the App ends your use of the service.

If you have further questions about these rights or wish to exercise them, please reach out via the contact methods in the "Contact Us" section below.

## 8. Storage Location and Retention

- **Storage location** — all data produced by the App lives **on your device**: Android `SharedPreferences` for preferences, the App sandbox directory for shared files, and process memory for session tokens and transfer counters. We do not maintain any of our own servers — inside or outside of any specific jurisdiction — that store your personal information.
- **Retention period** — unless otherwise required by law, your local data is kept until you uninstall the App, clear the App's data, or actively delete the corresponding files.

## 9. Contact Us

You can contact us via the following channel to exercise your rights; we will respond as soon as possible:

- **Email**: wh1990xiao2005@foxmail.com

If you are not satisfied with our response — particularly where you believe our information-handling behavior harms your lawful rights — you may also seek resolution through a court of competent jurisdiction, an industry self-regulatory body, or the relevant government regulator.

---

**Effective Date: July 7, 2026**

**By using WebDrop, you agree to this Privacy Policy.**
