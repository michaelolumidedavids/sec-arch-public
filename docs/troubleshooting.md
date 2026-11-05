# Troubleshooting

Find your problem in the list. If nothing here helps, [open an issue](../../../issues) and include your operating system and version, the SecArch version (**Help** menu, last line), and what you saw.

**Contents**

* [Windows](#windows)
* [macOS](#macos)
* [Using the app](#using-the-app)
* [Getting help](#getting-help)

## Windows

### The browser blocks or removes the download

Keep the file. In **Edge** open the Downloads panel (Ctrl+J), click the three dots beside the file, choose **Keep**, then **Show more** and **Keep anyway**. In **Chrome** choose **Keep**, then **Keep anyway**. See [Install on Windows](install-windows.md#your-browser-may-warn-about-the-download).

### "Windows protected your PC"

Click **More info**, then **Run anyway**. This warning appears because the installer is not yet signed by a publisher that Microsoft knows. See [Install on Windows, step 4](install-windows.md#4-run-the-installer-and-accept-the-windows-warning).

### There is no "Run anyway" button

Right click the installer, choose **Properties**, tick **Unblock** on the **General** tab, click **Apply** and **OK**, then run it again. Or run this in PowerShell, with your own path:

```powershell
Unblock-File "$env:USERPROFILE\Downloads\SecArch-Setup-0.1.0-x64.exe"
```

### Windows Security removed the installer

Open **Windows Security**, **Virus & threat protection**, **Protection history**, select the SecArch entry and choose **Allow on device** or **Restore**. Then run the installer again.

### The installer asks for an administrator password

You chose **Anyone who uses this computer (all users)**. Choose **Only for me** to install without administrator rights, or enter an administrator password.

### My company computer blocks the installer

Your IT team controls what can run. Ask them to allow `SecArch-Setup-0.1.0-x64.exe` (SHA256 in [`SHA256SUMS.txt`](../SHA256SUMS.txt)).

### Double clicking a `.secarc` file does not open SecArch

Right click the file, choose **Open with**, **Choose another app**, pick **SecArch**, and tick **Always use this app**.

## macOS

### "Not Opened" or "cannot be opened because it is from an unidentified developer"

This is Gatekeeper blocking an app that is not notarised by Apple. Click **Done** (not **Move to Bin**). Then open **System Settings, Privacy & Security**, scroll to **Security**, click **Open Anyway** beside the SecArch message, authenticate, and click **Open**. See [Install on macOS, step 4](install-macos.md#4-open-the-installer-and-accept-the-macos-warning).

### There is no "Open Anyway" button

1. Double click the file again so macOS records the block.
2. Open **System Settings, Privacy & Security** straight away and scroll to **Security**.
3. If it still is not there, use the [Terminal alternative](install-macos.md#7-terminal-alternative).

On a Mac managed by an employer, an administrator may have disabled the override. Ask IT.

### "SecArch is damaged and can't be opened. You should move it to the Bin"

The file is not damaged. macOS is reacting to the download mark. Run this in Terminal, then open the app again:

```sh
xattr -cr /Applications/SecArch.app
```

### Control click, then Open, does nothing

macOS 15 Sequoia and later removed that shortcut. Use **System Settings, Privacy & Security, Open Anyway**.

### "This package cannot be installed on this computer"

SecArch needs macOS 13 Ventura or later. Check **Apple menu, About This Mac**.

### The installer asks for a password

The app is installed into **Applications**, which needs an administrator password.

### Double clicking a `.secarc` file opens the wrong app

Select the file in Finder, press **Cmd+I**, under **Open with** choose **SecArch**, and click **Change All...**.

## Using the app

### My work is gone after closing the app

* Open the **Sessions** menu. SecArch keeps working sessions automatically. Click the latest one.
* Or reopen the app and click **Restore it** on the banner.
* Or use **File, Open Recent**.
* Next time, press **Ctrl or Cmd + S** to save to a `.secarc` file.

### The review shows few findings

The review can only judge what the design states. Check **Design Summary**, **Scope questions** (standards are switched on by your answers) and the **Completeness** list. Fill in the properties of your components and flows.

### A standard I expected is missing from the results

Open **Design Summary**, scroll to **Content packs**, and make sure the standard is ticked. Some standards (PCI DSS, the AI lists, DORA) switch on from the **Scope questions**.

### The threat model has no data flow diagram

It is built once you describe at least one relationship or journey step in **Design Summary, Design description**.

### AI assistance says it could not connect

Press **Test connection** in **AI settings**. Check the key, the model name and your internet connection. For Ollama, make sure Ollama is running and the model is downloaded. If the AI fails, the review still completes using the rules only and a short note says so. See [Optional AI assistance](ai-assistance.md).

### A download button does nothing

The app asks where to save the file. If you cancel the save window, nothing is saved. Click the button again.

### Where are my settings and sessions stored?

Choose **Help, Show app data folder**.

### How do I move my work to another computer?

Save as a `.secarc` file, copy it to the other computer, and open it with SecArch. You can also export the diagram as `.drawio` or PNG from **Generate Reports**.

## Getting help

[Open an issue](../../../issues). Please do **not** attach confidential designs or report files. Describe the problem in words, or use a small sample design.
