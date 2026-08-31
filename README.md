# agent-os-releases

Release downloads for Agent OS, a Windows desktop app for running and managing Claude Code sessions.

This repository holds no source code. It holds the published installers, and it is public so the
in-app updater can fetch them without a token. The application source lives in a private repository.
The installers are free to download and use under the end-user licence in `LICENSE.md`.

Agent OS is built for people who code. Several sessions across real projects, a terminal you live
in, notes in a vault. If your coding happens mostly on camera, there is nothing here for you; no
streamer mode, nothing that demos well, and every path in Settings is a typed text field.

## What each release contains

- `Agent OS_<version>_x64-setup.exe`, the per-user Windows installer.
- `Agent OS_<version>_x64-setup.exe.sig`, its minisign signature.
- `latest.json`, the update manifest the app reads. The app checks
  `https://github.com/teon-artilionAI/agent-os-releases/releases/latest/download/latest.json`.

## Before you install

These builds are NOT code signed yet. Windows SmartScreen will show a blue "Windows protected your
PC" screen the first time you run the installer, and you have to click "More info" and then
"Run anyway" to continue. That is expected for an unsigned build. It is also exactly what a
malicious installer looks like, so only run a file you downloaded from this repository, and check
that the URL in your address bar reads github.com/teon-artilionAI/agent-os-releases.

Every update the app downloads afterwards is verified against a minisign public key compiled into
the app before a single byte is installed, so the update path does not depend on SmartScreen. The
warning is about the FIRST install, which you perform yourself.

## Where it installs

Agent OS installs per user, into `%LOCALAPPDATA%\Agent OS`. Its data lives separately in
`%LOCALAPPDATA%\AgentOS` and updating never touches it.

## Found a problem, or want something?

Open an issue on this repository. Feature requests are welcome as issues too. For a problem
report, four things make it findable without a round trip:

1. What you did, in the order you did it.
2. What you expected and what happened instead.
3. The version, from the top of the Updates section in Settings.
4. The relevant log file from `%LOCALAPPDATA%\AgentOS\logs\`, named `agent-os.<date>.log`. Skim it
   before attaching; logs stay on your machine and are never uploaded by the app, so what you
   attach is your choice.