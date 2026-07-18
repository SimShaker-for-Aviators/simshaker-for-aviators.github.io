---
layout: page
title: SSA Manual
subtitle: Output Devices
before-content: manual-nav.html
---

<!-- Heading IDs below are linked from explore.html and may be linked from the app — do not rename. -->

The Output Devices page controls where SSA sends effects: a JetSeat/pad handler, the Sound Module, or both at once, plus massage mode.

Turning on JetSeat and Sound Module output independently gives you three possible states: JetSeat only, Sound Module only, or **simultaneous** output to both (when you enable the second device while the first is already on). SSA always requires at least one output to stay enabled — trying to turn both off is blocked with a message instead.

## JetSeat {#jetseat}

The JetSeat card ("JetSeat — USB") covers any pad-type device driven through a handler process, not just the Gametrix JetSeat itself:

- **Output to JetSeat** — the on/off switch for this output.
- **Handler** — which handler process to run: **JetSeat**, **ForceFeel** (used for Realteus ForceFeel and, in a limited capacity, the Next Level Racing HF8), or any additional handler shortcut SSA found in your settings folder (for example an installed SimShaker Pad Handler).
- **Restart** — kills and relaunches the selected handler process; useful if a device stopped responding without you changing any settings.
- **Test motors** — plays a short test pattern across all motors so you can confirm the device is wired up and receiving effects.

If you use the SimShaker Pad or the HF8Pro, they need the dedicated SimShaker Pad Handler software installed separately — SSA can start it, but can't substitute for it. See the [FAQ](../faq.html) for the download link.

## Sound Module {#sound-module}

The Sound Module card controls output to bass-shakers via the payware [SimShaker Sound Module](https://simshaker.com/software/general/sound/) add-on:

- **Output to Sound Module** — only enabled once SSA finds an installed Sound Module; if none is found, the switch is disabled and a warning explains that you need to [install the latest Sound Module application](https://dreamsimteam.blogspot.com/p/downloads.html).
- **Module** — which installed Sound Module shortcut to launch, if you have more than one.
- **Restart** — kills and relaunches the selected Sound Module.

## Massage mode {#massage-mode}

Massage mode plays a preset vibration pattern across your device(s) independent of any simulator — handy for testing hardware or just as a chair massage between flights.

- **▶ Start** begins the pattern; **■ Stop** ends it immediately.
- **Repetitions** sets how many times the pattern repeats per run (1–100).

## Device indicators {#device-indicators}

Both this page's device cards and the app's header dots reflect device state, but at different levels of detail:

- The **ACTIVE/OFF** label on each card here just reflects whether that output is *enabled* in settings.
- The **dots in the app header** go one step further and check whether the underlying handler or Sound Module process is actually running, using the same green/red/gray scheme everywhere in the app:
  - **Green** — the output is enabled and its handler/module process is running.
  - **Red** — the output is enabled, but SSA couldn't find its process running (it's "missing").
  - **Gray** — the output isn't enabled at all.

If a header dot is red, the fix is usually **Restart** on this page — or checking that the handler/Sound Module is actually installed for the option you selected.
