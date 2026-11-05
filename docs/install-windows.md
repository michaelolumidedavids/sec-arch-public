# Install SecArch on Windows

This guide installs SecArch Desktop on a Windows 10 or Windows 11 computer (64 bit). It takes about five minutes.

**Contents**

1. [Before you start](#1-before-you-start)
2. [Download the installer](#2-download-the-installer)
3. [Check the download (optional, recommended)](#3-check-the-download-optional-recommended)
4. [Run the installer and accept the Windows warning](#4-run-the-installer-and-accept-the-windows-warning)
5. [Complete the setup wizard](#5-complete-the-setup-wizard)
6. [Start SecArch](#6-start-secarch)
7. [If something goes wrong](#7-if-something-goes-wrong)
8. [Update or remove SecArch](#8-update-or-remove-secarch)

## 1. Before you start

| You need | Detail |
|---|---|
| Windows | Windows 10 or Windows 11, 64 bit (x64). |
| Download size | About 153 MB (160,211,500 bytes). |
| Account | None. SecArch has no sign in. |
| Internet | Only to download the installer. The app runs offline. |
| Permission | You can install for yourself without administrator rights. Installing for every user on the PC asks for an administrator password. |

**Work or managed computers.** If your PC is managed by an employer, your IT team may block programs that are not signed or are not on an approved list. If the steps below are blocked and there is no "Run anyway" button, ask IT to allow the installer. Do not try to get around a company policy.

## 2. Download the installer

1. Open the **[Releases page](../../../releases/latest)** of this repository.
2. Under **Assets**, click **`SecArch-Setup-0.1.0-x64.exe`**. (The version number in the name changes with each release.)
3. Your browser saves the file, normally into your **Downloads** folder.

### Your browser may warn about the download

Browsers warn about programs that are new or rarely downloaded. SecArch is a new program and is not yet signed with a paid publisher certificate, so a warning is expected. The wording differs between browsers and versions. In all of them, the choice you need is to **keep** the file.

* **Microsoft Edge:** open the Downloads panel (the arrow icon in the toolbar, or press **Ctrl+J**). Beside the file, click the **three dots (...)** and choose **Keep**. If Edge asks again, choose **Show more** and then **Keep anyway**.
* **Google Chrome:** open the Downloads panel and click **Keep**. If a second prompt appears, click **Keep anyway**.
* **Firefox:** open the Downloads panel and choose **Allow download** if it is offered.

Only keep the file if you downloaded it from this repository's Releases page.

## 3. Check the download (optional, recommended)

A checksum proves the file you have is exactly the file published here.

1. Open **PowerShell** (press the Windows key, type `PowerShell`, press Enter).
2. Run this command. Change the path if your file is somewhere else.

   ```powershell
   Get-FileHash "$env:USERPROFILE\Downloads\SecArch-Setup-0.1.0-x64.exe" -Algorithm SHA256
   ```

3. Compare the long value under **Hash** with the one for this file in [`SHA256SUMS.txt`](../SHA256SUMS.txt) or on the release page. They must match exactly:

   ```text
   44398177bbc4fe907f7042b8bf4f3e5c935ff57022ed3edf234cf3edaa460494  SecArch-Setup-0.1.0-x64.exe
   ```

If the values differ, delete the file and download it again. If they still differ, do not install it and open an issue.

## 4. Run the installer and accept the Windows warning

Double click **`SecArch-Setup-0.1.0-x64.exe`**.

### Windows shows "Windows protected your PC"

This is Microsoft Defender SmartScreen. It appears because the installer is not signed by a publisher that Microsoft already knows. It is not a finding that the program is harmful. You are choosing to trust this installer, so only continue if you got it from this repository.

1. In the blue **Windows protected your PC** window, the message reads: *Microsoft Defender SmartScreen prevented an unrecognized app from starting.* The visible button is **Don't run**. Do not click it.
2. Click the small link **More info**. The window expands and shows the file name and **Publisher: Unknown publisher**.
3. A new button **Run anyway** appears at the bottom. Click **Run anyway**.
4. If Windows shows **User Account Control** asking *Do you want to allow this app to make changes to your device?*, click **Yes**. This appears when you install for all users.

### There is no "Run anyway" button

Windows hides the button when the file carries a "downloaded from the internet" mark that your settings treat strictly. Remove the mark yourself:

**Option A, file properties**

1. Close the SmartScreen window.
2. Right click the installer and choose **Properties**.
3. On the **General** tab, tick **Unblock** next to **Security** (at the bottom).
4. Click **Apply**, then **OK**.
5. Double click the installer again.

**Option B, PowerShell**

```powershell
Unblock-File "$env:USERPROFILE\Downloads\SecArch-Setup-0.1.0-x64.exe"
```

Then double click the installer again.

### Windows Security (antivirus) removes or blocks the file

This is uncommon, but new unsigned programs are sometimes held back. If the file disappears from Downloads:

1. Open **Windows Security**, then **Virus & threat protection**, then **Protection history**.
2. Find the SecArch entry, open it, and choose **Actions**, then **Allow on device** (or **Restore**).
3. Download or run the installer again.

If your antivirus is a different product, use its quarantine list to restore the file.

## 5. Complete the setup wizard

1. **Install mode.** Choose **Only for me** (no administrator rights needed) or **Anyone who uses this computer (all users)** (asks for an administrator password). Click **Next**.
2. **Choose Install Location.** Keep the suggested folder or click **Browse...** to pick another. Click **Install**.
3. Wait for the progress bar to finish.
4. On the last page, leave **Run SecArch** ticked and click **Finish**.

The installer creates a **Desktop shortcut** and a **Start menu** entry named **SecArch**.

## 6. Start SecArch

* Double click the **SecArch** icon on your desktop, or open the **Start** menu and type `SecArch`.
* The app opens straight to the **Home** page. There is no sign in and no account.
* You should not see a Windows Firewall prompt. SecArch does not accept connections from other computers.
* Double clicking any file ending in **`.secarc`** now opens it in SecArch.

Next: read the **[User guide](user-guide.md)**.

## 7. If something goes wrong

| Problem | What to do |
|---|---|
| The browser will not keep the download | Use the steps under [Your browser may warn](#your-browser-may-warn-about-the-download). |
| SmartScreen shows no **Run anyway** | Use the [Unblock steps](#there-is-no-run-anyway-button). |
| The installer does not start after **Run anyway** | Right click it and choose **Run as administrator**. |
| The file vanished after downloading | Check Windows Security **Protection history** (see above). |
| A company policy blocks the installer | Ask your IT team. |
| SecArch opens but shows a blank window | Close it, start it again, and if it repeats, [open an issue](../../../issues) with your Windows version. |

More help: [Troubleshooting](troubleshooting.md).

## 8. Update or remove SecArch

* **Update:** download the newer installer from the Releases page and run it. It installs over the old version. Your saved files and session history are kept.
* **Remove:** open **Settings**, **Apps**, **Installed apps**, find **SecArch**, click the three dots and choose **Uninstall**. Your own `.secarc` files are never removed. Session history and settings stay in the app data folder (open **Help, Show app data folder** inside SecArch to find it before you uninstall).
