# Privacy and data

SecArch Desktop is built to keep your design on your computer.

## No account, no telemetry from the app

* There is no sign in and no account.
* The app does not send usage statistics.
* The app blocks every network request except the optional AI providers listed below, and your own computer (localhost) for Ollama.

## Where your data is

| What | Where |
|---|---|
| Your designs | The `.secarc` files you save, in folders you choose. |
| Automatic copies | The app keeps working sessions in its own data folder so you can return to them from the **Sessions** menu. |
| Settings | The app data folder. |

To open the app data folder, choose **Help, Show app data folder**. To remove stored sessions choose **Sessions, Clear session history**. **File, Open Recent, Clear recent files** clears the recent list.

A `.secarc` file is plain JSON. It contains your diagram, data register, review and threat model. Treat it as confidential if your design is.

## When data leaves your computer

Only when you switch on **AI assistance** and run a review or threat model. Then a description of the design goes to the provider you chose, as described in [Optional AI assistance](ai-assistance.md). With **Ollama (local)** nothing leaves your computer.

The only addresses the app allows are:

* `api.groq.com`, `generativelanguage.googleapis.com`, `openrouter.ai`, `api.anthropic.com`, `api.openai.com` (over HTTPS), used only if you enable that provider.
* `localhost`, `127.0.0.1` and `[::1]`, for Ollama on your own computer.

## Downloads from this repository

Downloading the installer from GitHub is subject to GitHub's own privacy terms. This repository contains installers and documentation only.

## About the content

The standards and rule sets inside the app are working content that is marked draft until a specialist reviews them against the published standards. A SecArch report supports a security review. It is not a certification, an audit opinion or legal advice.
