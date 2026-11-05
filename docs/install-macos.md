# Install SecArch on macOS

This guide installs SecArch Desktop on a Mac. It works on Apple silicon (M1 and later) and on Intel Macs with the same file. It takes about five minutes.

**Contents**

1. [Before you start](#1-before-you-start)
2. [Download the installer](#2-download-the-installer)
3. [Check the download (optional, recommended)](#3-check-the-download-optional-recommended)
4. [Open the installer and accept the macOS warning](#4-open-the-installer-and-accept-the-macos-warning)
5. [Run the installer](#5-run-the-installer)
6. [Open SecArch for the first time](#6-open-secarch-for-the-first-time)
7. [Terminal alternative](#7-terminal-alternative)
8. [If something goes wrong](#8-if-something-goes-wrong)
9. [Update or remove SecArch](#9-update-or-remove-secarch)

## 1. Before you start

| You need | Detail |
|---|---|
| macOS | macOS 13 Ventura or later. The installer refuses to run on older versions. |
| Chip | Apple silicon or Intel. One universal installer covers both. You do not need Rosetta. |
| Download size | About 254 MB (266,824,690 bytes). |
| Disk space | About 600 MB after installation. |
| Account | None. SecArch has no sign in. |
| Internet | Only to download the installer. The app runs offline. |
| Permission | An administrator password, because the app is installed into **Applications**. |

**Work or managed Macs.** If your Mac is managed by an employer, an administrator may have turned off the override described below. In that case the **Open Anyway** button does not appear and you need your IT team to approve the installer.

## 2. Download the installer

1. Open the **[Releases page](../../../releases/latest)** of this repository.
2. Under **Assets**, click **`SecArch-0.1.0-universal.pkg`**. (The version number in the name changes with each release.)
3. Safari, Chrome and Firefox save the file into your **Downloads** folder.

## 3. Check the download (optional, recommended)

A checksum proves the file you have is exactly the file published here.

1. Open **Terminal** (press **Cmd+Space**, type `Terminal`, press Return).
2. Run:

   ```sh
   shasum -a 256 ~/Downloads/SecArch-0.1.0-universal.pkg
   ```

3. Compare the result with [`SHA256SUMS.txt`](../SHA256SUMS.txt) or the release page. They must match exactly:

   ```text
   35876acbe070dfe2d09fb187b16bd6801e8f1ff22cb8d99c00d4dbf9e9576210  SecArch-0.1.0-universal.pkg
   ```

If the values differ, delete the file and download it again. If they still differ, do not install it and open an issue.

## 4. Open the installer and accept the macOS warning

SecArch is not yet signed with an Apple Developer ID and has not been notarised by Apple. macOS Gatekeeper therefore blocks it the first time. This is not a finding that the program is harmful. You are choosing to trust this installer, so only continue if you got it from this repository.

### Step 4a. Try to open it once

1. In **Finder**, open **Downloads** and double click **`SecArch-0.1.0-universal.pkg`**.
2. macOS shows a message that starts with the file name, for example:

   > **"SecArch-0.1.0-universal.pkg" Not Opened**
   > Apple could not verify "SecArch-0.1.0-universal.pkg" is free of malware that may harm your Mac or compromise your privacy.

   On older versions the wording is *"cannot be opened because it is from an unidentified developer"* or *"Apple cannot check it for malicious software"*. The meaning is the same.
3. Click **Done** (or **OK**). **Do not click Move to Bin** (called Move to Trash on older macOS). That deletes the installer.

This step is required. macOS only offers the override after you have tried to open the file.

### Step 4b. Allow it in System Settings

1. Open the **Apple menu** at the top left and choose **System Settings**.
2. Click **Privacy & Security** in the sidebar.
3. Scroll down to the **Security** section. You will see a line such as:

   > "SecArch-0.1.0-universal.pkg" was blocked to protect your Mac.

   with a button **Open Anyway**.
4. Click **Open Anyway**.
5. Enter your Mac password or use **Touch ID** when asked.
6. A final warning appears. Click **Open** (the wording may be **Open Anyway**). The installer starts.

If you do not see **Open Anyway**, go back to Step 4a and double click the file again, then reopen **Privacy & Security**. The option only stays available for a limited time after the blocked attempt.

> **macOS 15 Sequoia and later.** Control clicking a file and choosing **Open** no longer bypasses the block. Use the **System Settings** route above. On macOS 13 and 14 you can also Control click the file, choose **Open**, then click **Open** in the dialog.

## 5. Run the installer

1. On **Introduction**, click **Continue**.
2. If shown a licence or destination page, click **Continue** or **Agree**, and keep the default destination. SecArch installs into **Applications** for all users of the Mac.
3. Click **Install**.
4. Enter your administrator password and click **Install Software**.
5. When it says **The installation was successful**, click **Close**.
6. If asked whether to move the installer to the Bin, you can choose either. Keep it if you want to reinstall later.

## 6. Open SecArch for the first time

1. Open **Finder**, then **Applications**, and double click **SecArch**. You can also use **Launchpad** or Spotlight (**Cmd+Space**, type `SecArch`).
2. If macOS blocks the app with a similar message (*"SecArch" Not Opened*), click **Done** and repeat Step 4b. This time **Privacy & Security** shows *"SecArch" was blocked to protect your Mac*. Click **Open Anyway**, authenticate, and click **Open**.
3. If macOS says **"SecArch" is damaged and can't be opened. You should move it to the Bin**, do not move it. This message means the download mark is blocking the app. Clear the mark with the Terminal command in [section 7](#7-terminal-alternative), then open the app again.
4. After the first successful open, macOS remembers your choice and you can open SecArch by double clicking as normal.
5. The app opens straight to the **Home** page. There is no sign in and no account. Double clicking any **`.secarc`** file now opens it in SecArch.

Next: read the **[User guide](user-guide.md)**.

## 7. Terminal alternative

If you prefer the command line, or the **Open Anyway** button does not appear, these commands do the same job. Run them in **Terminal**. Change the path if your file is not in Downloads.

Remove the download mark from the installer, then install it:

```sh
xattr -d com.apple.quarantine ~/Downloads/SecArch-0.1.0-universal.pkg
sudo installer -pkg ~/Downloads/SecArch-0.1.0-universal.pkg -target /
```

(If the first command prints *No such xattr*, the mark is already gone. Continue with the second command.)

If the app itself is blocked or reported as damaged, clear its mark:

```sh
xattr -cr /Applications/SecArch.app
```

Then open SecArch from **Applications**.

## 8. If something goes wrong

| Problem | What to do |
|---|---|
| No **Open Anyway** button in System Settings | Double click the file again, then reopen **Privacy & Security** straight away. Or use the [Terminal alternative](#7-terminal-alternative). |
| "Not Opened" message has no way forward | Click **Done**, then follow Step 4b. The override is in System Settings, not in the message box. |
| "SecArch is damaged and can't be opened" | Run `xattr -cr /Applications/SecArch.app`, then open the app again. |
| The installer says it cannot be installed on this computer | Your macOS is older than 13. Update macOS or use another computer. |
| **Open Anyway** is greyed out or missing on a work Mac | An administrator controls this. Ask IT to allow SecArch. |
| Control click **Open** does nothing | On macOS 15 and later this shortcut was removed. Use System Settings. |

More help: [Troubleshooting](troubleshooting.md).

## 9. Update or remove SecArch

* **Update:** download the newer `.pkg` from the Releases page and run it. It replaces the app in **Applications**. Your saved files and session history are kept.
* **Remove:** quit SecArch, then drag **SecArch** from **Applications** to the Bin. Your own `.secarc` files are never removed. Session history and settings stay in the app data folder (open **Help, Show app data folder** inside SecArch to find it before you delete the app, and delete that folder too if you want a full clean up).
