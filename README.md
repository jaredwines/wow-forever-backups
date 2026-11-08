

\# WoW Forever Backups



A personal backup repository for \*\*World of Warcraft: Forever\*\*, using \*\*WoWUp\*\* and Blizzard's built-in UI layout export feature.



Backups are organized separately for three devices:



\- \*\*PC\*\* — Windows 11

\- \*\*Mac\*\* — macOS

\- \*\*Steam Deck\*\* — SteamOS



Git provides version history, allowing older configurations to be recovered.



\## Backup Contents



This repository stores two types of backups.



\### 1. WoWUp Backups



WoWUp's Interface Settings Backup feature saves the World of Warcraft `WTF` folder.



This generally includes:



\- Addon settings and profiles

\- SavedVariables

\- Local character settings

\- Keybindings and macros

\- Graphics and audio preferences

\- Other locally stored game configuration



\*\*Note:\*\* WoWUp's settings backups do not include the installed addon files themselves. Missing addons must be reinstalled separately.



\### 2. Blizzard UI Layout Backups



Blizzard's Edit Mode allows UI layouts to be exported as text strings.



These backups preserve customized interface layouts that can later be imported into WoW Forever.



UI layout exports do not include addon settings, macros, keybindings, or graphics settings.



\## Repository Structure



```text

wow-forever-backups/

├── pc/

│   ├── wowup-backup/

│   └── ui-layouts-backup/

├── mac/

│   ├── wowup-backup/

│   └── ui-layouts-backup/

├── steam-deck/

│   ├── wowup-backup/

│   └── ui-layouts-backup/

└── blastoise/

```


Empty directories are preserved using `.gitkeep` files.



\## Creating a Backup



\### Step 1: Export Your UI Layout



1\. Launch WoW Forever.

2\. Open \*\*Esc → Edit Mode\*\*.

3\. Select your preferred layout.

4\. Use \*\*Share / Export\*\* to copy the layout string.

5\. Paste the string into a `.txt` file.

6\. Save the file in the appropriate device's `ui-layouts-backup/` folder.

7\. Close WoW Forever.



Use descriptive filenames, such as:



`2026-11-08-hunter-ui.txt`



\### Step 2: Create a WoWUp Backup



1\. Open WoWUp.

2\. Select \*\*World of Warcraft: Forever\*\*.

3\. Open \*\*My Addons → Interface Settings Backup\*\*.

4\. Select \*\*Create Backup\*\*.

5\. Click \*\*Show Folder\*\*.

6\. Copy the new backup into the matching device's `wowup-backup/` folder.



Preserve WoWUp's original backup filenames and directory structure.



\### Step 3: Push to GitHub



From your local repository, stage the files for the appropriate device.



For Windows:



```powershell

git add pc/

git commit -m "Backup WoW Forever PC settings"

git push

```



For Mac:



```bash

git add mac/

git commit -m "Backup WoW Forever Mac settings"

git push

```



For Steam Deck:



```bash

git add steam-deck/

git commit -m "Backup WoW Forever Steam Deck settings"

git push

```



Pull the latest changes before creating new backups, and avoid modifying the same repository simultaneously on multiple devices.



\## Restoring Backups



\### Restore WoWUp Settings



1\. Find the desired backup in the repository.

2\. Download or copy its WoWUp backup file.

3\. Close WoW Forever.

4\. Create a safety backup of your current settings.

5\. Open WoWUp's backup directory using \*\*Show Folder\*\*.

6\. Place the downloaded backup in the appropriate location.

7\. Select the backup in WoWUp and apply it.

8\. Launch WoW Forever and verify your settings.



Reinstall missing addons through WoWUp if necessary.



\### Restore Blizzard UI Layouts



1\. Open the saved UI layout text file.

2\. Copy the exported layout string.

3\. Launch WoW Forever.

4\. Open \*\*Esc → Edit Mode → Import\*\*.

5\. Paste the string.

6\. Name and save the imported layout.



Layouts may need adjustments when transferred between devices with different resolutions or input methods.



\## Recommended Backup Schedule



Create backups:



\- Once per week on devices you use

\- Before major addon changes

\- Before major UI modifications

\- After completing a preferred UI layout

\- After significant game updates



Keep older backups to preserve version history.



\## Limitations



\- Backups are created manually.

\- There is no automatic cross-device synchronization.

\- Installed addon program files are not included.

\- UI export strings preserve layouts, not complete game settings.

\- Steam Input controller mappings are not included.

\- Git history can grow as additional compressed backups are committed.



GitHub limits regular Git files to 100 MiB. Consider GitHub Releases for larger backup archives.



\## Security



WoWUp backups may contain personal information or sensitive addon configuration.



\*\*Keep this repository private.\*\*



Do not commit passwords, authentication tokens, SSH keys, or other credentials.



Enable two-factor authentication on your GitHub account.



\## Resources



\- \[WoWUp](https://wowup.io/)

\- \[WoWUp Backup Guide](https://wowup.io/guide/my-addons/addon-settings)

\- \[Blizzard Edit Mode](https://worldofwarcraft.blizzard.com/en-us/news/23837944)

\- \[Git Documentation](https://git-scm.com/doc)



