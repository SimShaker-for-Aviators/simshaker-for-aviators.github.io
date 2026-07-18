---
layout: page
title: SSA Manual
subtitle: Settings
before-content: manual-nav.html
---

<!-- Heading IDs below are linked from explore.html and may be linked from the app — do not rename. -->

The Settings page groups everything that isn't per-aircraft into cards: updates, folder shortcuts, performance, the SSA Tester launcher, backup/restore, a danger zone, community links, and a live application log.

## Updates {#updates}

**Check for updates on startup** toggles automatic update checks; leave it on to be notified when a new release is available. SSA always checks against the track you installed — a stable install checks for new stable releases, a beta install checks for new beta releases, and so on. The card also shows your current version string.

## Folders {#folders}

Three shortcuts open Windows Explorer directly at:

- **SSA Install Folder** — where the application itself is installed.
- **SSA Config Folder** — where your settings database and logs live.
- **DCS Export Folder** — your DCS `Saved Games\...\Scripts` folder (checked against both the release and open-beta locations); shows a warning if no DCS folder can be found.

The current config folder path is shown under the buttons.

## Performance {#performance}

The **Frame rate limiter** controls how often incoming telemetry is processed: **None**, **100 ms**, or **250 ms**. Raising it reduces CPU load on slower systems at the cost of slightly less frequent effect updates — worth trying if you notice stutter with SSA running alongside a demanding simulator.

## SSA Tester {#tester}

**↗ Launch SSA Tester** starts the standalone SSA Tester application, a companion tool for recording and replaying simulator telemetry — handy for testing effects without needing the simulator running. See the full [SSA Tester manual](../tester.html) for what it can do.

## Backup & restore {#backup-restore}

- **Export…** saves your entire settings database (all profiles and settings) to an XML file you choose.
- **Import…** loads a settings database back in. It accepts both the current XML format and legacy v2 `.bin` files, auto-detecting which one you picked.

Importing replaces your current settings database — export first if you want to keep a copy of what you have.

## Danger zone {#danger-zone}

**Reset Settings Database…** wipes all profiles and settings back to factory defaults. This cannot be undone, and SSA asks for confirmation before doing it — use [Export…](#backup-restore) first if there's any chance you'll want your current setup back.

## Help & community {#help-community}

Quick links to the **Changelog**, the [FAQ](../faq.html), the [project website](../index.html), the project [Discord](https://discord.gg/jkadGQbNj3), a **Support the project** mail link, and the **About** dialog. SimShaker for Aviators is free — these links are also where to reach out if you want to support development or need help.

## Application log {#log}

A live view of SSA's application log, useful for troubleshooting without digging through log files by hand.

- Toggle verbose logging to include Debug-level messages, not just warnings/errors — useful when reproducing a problem, but generating them has a small performance cost, so switch it back off afterwards.
- **Pause** freezes the view so you can read a specific moment without new lines pushing it away.
- **Copy** puts the current log to the clipboard, and **Clear** empties the view.
- The log can be popped out into its own window if you want it visible alongside another page.

The same log files are also written to disk in your SSA config folder (see [Folders](#folders)) — the [FAQ](../faq.html) covers how to raise their verbosity permanently via `NLog.config`.
