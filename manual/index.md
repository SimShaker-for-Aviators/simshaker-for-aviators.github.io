---
layout: page
title: SSA Manual
subtitle: Overview
before-content: manual-nav.html
---

<!-- Heading IDs below are linked from explore.html and may be linked from the app — do not rename. -->

SimShaker for Aviators (SSA) turns flight-sim telemetry into tactile feedback. It reads live data from your simulator, runs it through a per-aircraft set of effects (engine rumble, turbulence, gear, weapons, damage, and more), and drives that feedback out to a Gametrix JetSeat or the payware SimShaker Sound Module.

This manual documents the **new WPF UI** (currently a preview, running alongside the classic interface). If you're still on the classic UI, the PDF manual bundled with your installation covers it — see the note at the bottom of this page.

## Supported simulators and devices

- **Simulators:** DCS World, X-Plane 11/12, Microsoft Flight Simulator 2020/2024, Microsoft Flight Simulator X, Prepar3D
- **Devices:** Gametrix JetSeat, SimShaker JetPad, SimShaker Pad, Realteus ForceFeel, Next Level Racing HF8 (limited, via ForceFeel), and 1–6 bass-shakers through the payware [SimShaker Sound Module](https://simshaker.com/software/general/sound/)

For the full, always-current list see the [project home page](/index.html).

## Installation {#installation}

1. Download the installer for the release track you want (stable, beta, or alpha) from the [home page](/index.html). SSA 3 alpha uses a new settings format that is **not** compatible with SSA 2 — if you're moving from SSA 2, plan on reconfiguring your profiles.
2. Run the installer and start SimShaker for Aviators.
3. SSA automatically maintains the DCS export script and offers to install the MSFS WASM bridge and X-Plane plugin the first time it needs them — see [First run](#first-run) below.
4. If you use a JetSeat or another pad, install and connect it before starting SSA so the handler can detect it — device setup is covered in [Output Devices](devices.html).

Once installed, SSA checks for updates on startup by default (this can be turned off in [Settings](settings.html#updates)) and always checks against the track you installed — stable stays on stable, beta stays on beta.

## First run {#first-run}

What happens the first time SSA talks to each simulator:

- **DCS World** — SSA writes its entry into DCS's `Export.lua` automatically on startup; no manual step is needed. If DCS never connects, see [Connections → DCS](connections.html#dcs) and the [troubleshooting section](connections.html#troubleshooting).
- **X-Plane** — SSA does *not* install its plugin automatically. Enable "Support enabled" on the [Connections page](connections.html#xplane) and point it at your `X-Plane.exe`; SSA copies the plugin into your X-Plane installation for you.
- **MSFS** — the core connection uses SimConnect and needs no setup. Some third-party aircraft expose extra data only through custom LVARs, which requires installing the SSA WASM Bridge into your Community folder. That's an opt-in toggle on the [Connections page](connections.html#msfs).

## 60-second UI tour {#ui-tour}

The new UI is a single window with four areas:

| Area | What it shows |
|---|---|
| Title bar | Custom window chrome — minimize, maximize, close, and the current version. |
| Status header | Sim connection chips on the left (DCS, X-Plane, MSFS), device dots on the right (JetSeat, Sound Module). |
| Sidebar | Four pages: **Aircraft Effects**, **Connections**, **Output Devices**, **Settings**. |
| Toast overlay | Brief confirmation messages (e.g. after copying a profile) that fade automatically. |

The **sim chips** in the header light up green the moment SSA is receiving data from that simulator; otherwise they sit idle/gray. The **device dots** follow a three-state scheme used throughout the app — green means the output is enabled and its handler process is actually running, red means it's enabled but the handler couldn't be found, and gray means the output isn't enabled at all. The same scheme is explained in detail under [Output Devices → Device indicators](devices.html#device-indicators).

Everything in the new UI operates on the same settings database and effect engine as the classic UI, so you can switch between them freely — changes made in one show up in the other.

<div style="border:1px solid rgba(127,127,127,.35); border-radius:8px; padding:14px 18px; margin:1.5rem 0;">
  <strong>Want to click through it instead?</strong><br />
  <a href="explore.html">Explore the UI interactively →</a>
</div>

## Using the classic UI

This manual covers the new WPF preview only. If you're using the classic (default) interface, the legacy PDF manual bundled with your installation documents it.
