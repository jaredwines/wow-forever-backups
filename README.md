# WoW Forever Backups

A personal, versioned backup repository for **World of Warcraft: Forever**, using **WoWUp** settings backups, **WoWUp addon-list exports**, and Blizzard's built-in **Edit Mode UI layout exports**.

Backups are organized separately for three devices:

- **PC** — Windows 11
- **Mac** — macOS
- **Steam Deck** — SteamOS

Git records changes over time, allowing you to recover an earlier backup. Backups are created manually; settings are **not automatically synchronized** between devices.

> [!WARNING]
> **Protect your data:** This repository was public when last checked. WoWUp settings archives can contain account identifiers, character information, or addon configuration. Change the repository visibility to **Private** before uploading more backups.

## What Gets Backed Up?

### WoWUp settings backups

WoWUp's **Interface Settings Backup** feature saves the game's `WTF` folder, which generally contains:

- Addon settings and profiles (SavedVariables)
- Local character and account settings
- Keybindings and locally stored macros
- Graphics and audio preferences
- Other locally stored game configuration

**Important:** WoWUp's settings backup does **not** include the installed addon files themselves. Reinstall missing addons through WoWUp before restoring their settings.

### WoWUp addon-list exports

WoWUp's **Import / Export Addons** feature produces a text string listing installed addons. This is useful for reinstalling the same addon collection after rebuilding a computer. It does not contain addon settings or the addon files themselves.

### Blizzard UI layout backups

Blizzard's **Edit Mode** can export a UI layout as a text string. Saving that string lets you import the layout again later, including when some layout information is stored outside the local `WTF` folder.

UI strings do **not** contain your complete addon settings, macros, keybindings, graphics, or audio settings.

## Repository Structure

```text
wow-forever-backups/
├── pc/                         
│   ├── wowup-backup/
│   │   └── wtf_backups/
│   │       └── <client-id>/
│   │           └── wtf_*.zip
│   └── ui-layouts-backup/
│       └── pc-ui.txt      
├── mac/
│   ├── wowup-backup/
│   │   ├── Addons Backup/
│   │   │   └── addons-import-text.txt
│   │   └── Interface Settings Backup/
│   │       └── wtf_*.zip
│   └── ui-layouts-backup/
│       └── mac-ui.txt
└── steamdeck/                  
    ├── wowup-backup/
    │   └── wtf_backups/
    │       └── <client-id>/
    │           └── wtf_*.zip
    └── ui-layouts-backup/
        └── steamdeck-ui.txt

```

Use **`pc/` for Blastoise** and **`steamdeck/` for Steam Deck**. The similarly named `blastoise/` and `steam-deck/` folders are currently placeholders; don't split active backups across both spellings.

Empty directories are preserved with `.gitkeep` files.

## Creating a Backup

Repeat these steps on each computer you want to back up.

### 1. Export your UI layout

1. Launch **WoW Forever**.
2. Open **Esc → Edit Mode**.
3. Select the layout you want to save.
4. Use **Share / Export** to copy the layout string.
5. Paste the complete string into a plain-text file, such as `mac-ui.txt`, `steamdeck-ui.txt`, or a dated layout name.
6. Save it in that device's `ui-layouts-backup/` directory.
7. Log out and **close WoW Forever**.

If you use different keyboard-and-mouse and gamepad layouts, export them into separately named text files.

### 2. Export your addon list with WoWUp

1. In WoWUp, select **World of Warcraft: Forever**.
2. Open **My Addons → Import / Export Addons** and select **Export**.
3. Copy the addon string to a plain-text file under that device's `wowup-backup/` folder. On Mac, the existing location is `Addons Backup/addons-import-text.txt`.
4. Update the export when you add or remove addons.

### 3. Create a WoWUp settings backup

1. Open **WoWUp** and select **World of Warcraft: Forever**.
2. Go to **My Addons → Interface Settings Backup**.
3. Select **Create Backup**, then **Show Folder**.
4. Copy the new backup into that device's `wowup-backup/` directory. Keep the existing device-specific subfolder arrangement.
5. Keep the original backup filename and any necessary WoWUp folder structure. Leave the original local backup in place.

### 4. Commit and push to GitHub

Pull the latest repository changes **before** copying in new backups. Then, from the root of your local repository, stage the appropriate device directory.

**Blastoise (PowerShell):**

```powershell
git add pc/
git commit -m "Backup WoW Forever PC settings"
git push
```

**Mac (Terminal):**

```bash
git add mac/
git commit -m "Backup WoW Forever Mac settings"
git push
```

**Steam Deck (Desktop Mode terminal):**

```bash
git add steamdeck/
git commit -m "Backup WoW Forever Steam Deck settings"
git push
```

If your Git working directory also lives inside **Seafile**, avoid editing it on two devices simultaneously. Let one device finish synchronizing before making Git changes from another.

## Restoring a Backup

### Restore WoWUp settings

1. Find the desired backup for the correct device in this repository or Git history.
2. Download or copy the corresponding WoWUp backup file.
3. **Close WoW Forever completely.**
4. Make a new WoWUp backup of your current settings as a safety copy.
5. In WoWUp, select **Interface Settings Backup → Show Folder**.
6. Place the downloaded backup in the appropriate WoWUp backup directory.
7. Reopen the backup dialog if needed, select the backup, and **Apply** it.
8. Reinstall any missing addons through WoWUp. If you saved an addon-list text export, paste it into **My Addons → Import / Export Addons → Import**, then install the listed addons.
9. Launch WoW Forever and verify your settings.

### Restore a Blizzard UI layout

1. Open the saved `.txt` file and copy its complete UI export string.
2. Launch WoW Forever and open **Esc → Edit Mode → Import**.
3. Paste the string, name the imported layout, and save it.

Layouts may need adjustments between Blastoise, Mac, and Steam Deck because screen resolutions, UI scale, and controller settings differ.

## Recommended Backup Schedule

Create a backup:

- **Weekly** for each device you used
- **Before** changing important addons or UI layouts
- **After** finishing a UI setup you want to keep
- **After** a major WoW Forever update, once the setup works correctly

Keep older backups so previous versions remain recoverable. Periodically test that a backup can be downloaded and restored.

## Limitations and Security

- Backup creation and Git uploads are **manual**.
- This repository does **not** automatically sync settings between devices.
- Addon-list exports record what to install, not the installed files. Steam Input controller mappings are **not** included.
- Repeated ZIP backups can make Git history grow quickly. GitHub blocks regular Git files larger than **100 MiB**; consider Release attachments if archives become too large.
- WoWUp backups can contain account identifiers, character names, or sensitive addon data. **Keep the GitHub repository private**, use two-factor authentication, and never commit passwords, tokens, or private SSH keys.

## Resources

- [WoWUp](https://wowup.io/)
- [WoWUp — Interface settings backups](https://wowup.io/guide/my-addons/addon-settings)
- [WoWUp — Import and export addon lists](https://wowup.io/guide/my-addons/addon-import)
- [WoWUp — Game clients](https://wowup.io/guide/options/wow-clients)
- [Blizzard — Updated UI and HUD / Edit Mode](https://worldofwarcraft.blizzard.com/en-us/news/23837944)
- [GitHub — About large files](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github)
