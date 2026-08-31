# agent-os-releases

<p align="center"><img src="assets/agent-os-logo.png" width="160" alt="The Agent OS emblem"></p>

Release downloads for **Agent OS**, a Windows desktop workspace for people who run coding agents.

If you work with Claude Code, Codex, OpenCode, Pi or Antigravity, you know the shape of the
problem. Five terminals, each holding an agent that might be busy, might be waiting on your
answer, or might have finished twenty minutes ago without you noticing. Agent OS puts all of
them in one window and tells you, honestly, what each one is doing.

What it gives you.

- **A live dashboard.** Every coding agent session on the machine, marked by agent, shown as
  busy, waiting or idle only when its own files prove it, with the evidence named in the
  tooltip. A recent list shows what just ended, what it cost where the agent reports cost, and
  a Resume button that reopens the conversation.
- **Terminals for every agent.** Real shells and real agent tabs side by side in a resizable
  mosaic. Spawn a Claude, Codex, OpenCode, Pi or Antigravity tab in any folder, continue that
  folder's most recent conversation, or fork one where the CLI supports it.
- **Runs without babysitting.** A kanban board and a quick prompt that launch headless runs on
  any of the five agents, with each CLI's real model list, permission modes and effort levels,
  and a budget cap where the agent reports spend. Drag a card to In Progress, press Start,
  watch the status and the cost on the card.
- **Your history, searchable.** Claude Code transcripts are imported into a local archive with
  search across every conversation the CLI ever wrote, so nothing an agent said is lost.
- **Notes where you work.** A markdown vault workspace beside the terminals, for the thinking
  that surrounds the sessions.

Everything stays on your machine. Transcripts and agent stores are read from your own disk, the
database is local SQLite, and the one automatic network call is the update check against this
repository, described below.

This repository holds no source code. It holds the published installers, and it is public so the
in-app updater can fetch them without a token. The application source lives in a private
repository. The installers are free to download and use under the end-user licence in
`LICENSE.md`.

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