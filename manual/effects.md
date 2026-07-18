---
layout: page
title: SSA Manual
subtitle: Aircraft Effects
before-content: manual-nav.html
---

<!-- Heading IDs below are linked from explore.html and may be linked from the app — do not rename. -->

The Aircraft Effects page is where you pick an aircraft profile and tune every effect for it — what's on, how strong it is on each output device, and (for a handful of effects) extra parameters. It's the page SSA opens on by default.

## Choosing a simulator and aircraft {#simulator-aircraft}

Two dropdowns sit at the top of the page:

- **Simulator** — the game whose profiles you're editing (DCS, X-Plane, MSFS/FSX, Prepar3D, …).
- **Aircraft** — the profile within that simulator.

Whichever aircraft is currently active *in the simulator* is marked with a small accent dot and highlighted text in both dropdowns, so you can always find it quickly even in a long list. A pill on the right of the pickers, labeled **In sim**, shows the detected aircraft and its type at a glance; it turns from red/"none" to accent-colored the moment SSA recognizes an aircraft in the sim. Selecting a different profile than the one you're flying is completely fine — it just means you're editing settings for an aircraft that isn't currently active.

If an aircraft isn't individually supported yet, SSA falls back to a **generic profile** (generic jet, piston, turboprop, or helicopter) so you still get baseline effects.

Use **↻ Reload** if you've added new aircraft to the settings database from elsewhere (e.g. the classic UI) and want the pickers to pick them up without restarting.

## The effect table {#effect-table}

The table lists every effect available for the selected profile, one row per effect:

| Column | What it does |
|---|---|
| Chevron | Expands the row to show parameters (only present on effects that have any — see [Parameters](#parameters)). |
| Effect name | The effect's display name. A small amber dot lights up next to it while the effect is actively firing. |
| ON | Master on/off switch for that effect. |
| JETSEAT | Volume slider (with a live activity bar underneath) and the resulting value, sending to the JetSeat/pad output. |
| SOUND MODULE | Same as JetSeat, but for the Sound Module output. |

The JetSeat and Sound Module columns only appear when that output is actually enabled — see [Output Devices](devices.html). If you've only enabled one device, the table simply hides the other column rather than showing disabled sliders. Disabled effects (ON switched off) show their name faded out, and their volume controls dim, but stay visible so you can still see and change their configured level.

## Expanding rows and parameter kinds {#parameters}

Effects with tunable extras show a small chip (e.g. "Parameters" or "Configurator") next to their name — click the chevron or the chip to expand the row and reveal them inline. Three kinds of inline controls are used, plus one effect (Turbulence) that gets its own embedded editor instead:

| Kind | Control | Used for |
|---|---|---|
| Stepper | Up/down arrows on an integer value | Filters and thresholds expressed as whole numbers, e.g. a movement filter or a damping percentage. |
| Slider | A small draggable slider with a snapped step | Fractional values, e.g. G-force deadzones. |
| Toggle | A checkbox | On/off sub-options for an effect. |
| External | No inline control — opens the dedicated configurator | Currently only Turbulence; see [Turbulence editor](#turbulence). |

A few examples of what you'll actually find when you expand a row:

- **Engine Rumble/Piston Beat** — "Reduce when airborne (%)" stepper, to tone the effect down once you're off the ground.
- **Flaps Movement** / **Slats Movement** — a "Movement filter" stepper that smooths out how the effect responds to flap/slat travel.
- **Buffet/Stall Shudders** — a "Cockpit shaking filter" stepper.
- **G-Force Effect** — two deadzone sliders (negative and positive G, in g-units), plus toggles to ignore roll-induced G, keep the effect active on the ground, or switch it off entirely while airborne.

Any changes you make in an expanded row are part of the profile like everything else in the table — they're included in [Save / Reset / Copy](#copy-reset).

## Turbulence editor {#turbulence}

Turbulence is the one effect with a full embedded configurator instead of a handful of inline fields, because tuning it benefits from seeing live data. Expanding the Turbulence row shows:

- **Threshold** and **Threshold strong** — the input level (in delta wind speed, knots) at which turbulence starts, and at which it's considered "strong". Both are steppers with a 0.05 step.
- **Min effect strength** and **Max effect input** — reshape the low and high end of the response curve.
- **Filter function** — a dropdown with three response curves: **Linear**, **Cubic (ease-out)**, and **Quadratic**. This decides how input wind maps to output strength between the threshold and the max input.
- **Reset filter** — restores all of the above to SSA's defaults (Threshold 0.1, Threshold strong 0.5, Min effect strength 0, Max effect input 1, filter Linear).

Below the controls are three live charts, useful while you're actually flying the profile you're editing:

1. **Turbulence input — delta V_wind [kts]** — the raw input signal over time, with the two threshold lines overlaid.
2. **Filter function** — a preview of the selected curve, with a crosshair showing where your current live input lands on it.
3. **Resulting effect strength** — the final output value sent to your devices.

Until you start flying the matching profile, all three charts show a "start flying to see live data" placeholder instead of a live trace — the controls above them work regardless.

## Save, reset and copy {#copy-reset}

The footer below the table has three actions:

- **Save profile** — writes the whole settings database to disk. The button briefly shows "✓ Saved" as confirmation.
- **Reset** — reverts every effect on the currently displayed profile back to its last-saved state, discarding unsaved edits. Both Save and Reset are only enabled while the profile actually has unsaved changes.
- **Copy settings…** — opens a dialog to copy the *current* profile's settings elsewhere, useful once you've tuned one aircraft and want to reuse that tuning. You get three targets:
  - **[Aircraft type] template** — newly detected aircraft of that type (e.g. any new generic jet) will start from these settings. Only shown when a template exists for the type.
  - **Another aircraft** — pick one specific aircraft from a dropdown and overwrite its saved settings.
  - **All [aircraft type]s** — overwrite every aircraft of the same type at once; the dialog lists which aircraft are affected and shows a warning before you confirm, since this can't be undone.

Copying writes the database to disk immediately, the same as Save profile.

## Effect glossary {#effect-glossary}

Every effect currently defined in SSA, grouped the same way the settings database groups them. Not every aircraft implements every effect — the table only shows what's relevant to the selected profile.

### Engine effects

- **Engine Rumble/Piston Beat** — vibration while the engine runs; piston engines get a beat-like pulse, turbines a steadier rumble.
- **Main Rotor Whirl Low** — vibration of a helicopter's main rotor spinning up at low/idle RPM.
- **Main Rotor Whirl High** — vibration of the main rotor at full operating RPM.
- **Afterburner/WEP** — the extra kick of afterburner (jets) or War Emergency Power (piston engines).
- **APU Rumble** — vibration from the auxiliary power unit, on aircraft that model one.

### Ground effects

- **Ground Bumps** — vibration from rolling over an uneven runway or taxiway surface.
- **Touchdown** — the impact felt when the main gear first contacts the runway.
- **Wheel Blocking** — a skid/lock-up feel when the wheels stop turning under heavy braking.
- **Ground Roll** — general vibration while taxiing or rolling on the ground.

### Buffet and stall effects

- **Buffet/Stall Shudders/Vortex Ring State** — vibration from an aerodynamic stall, or (for helicopters) from entering a vortex ring state.
- **Low Buffet** — a lighter buffet ahead of a full stall, on aircraft that model an early warning stage separately.
- **High Speed Shudders** — airframe shudder felt at high airspeed or Mach number.

### Aircraft systems

- **Speedbrake Shudders** — vibration while the speedbrakes or spoilers are deployed.
- **Flaps Movement** — vibration while the flaps are in transit; has a Movement filter parameter (see [Parameters](#parameters)).
- **Landing Gear Up/Down** — vibration while the gear extends or retracts.
- **Canopy/Door Open/Close** — vibration while a canopy or door opens or closes.
- **Dashboard/Canopy Shake** — jolting of the instrument panel, on aircraft that model that separately from the general airframe.
- **Dragchute** — vibration when a drag/brake parachute deploys.
- **Seat Ejection** — vibration at the moment of ejection.
- **SPS** — the kick of the MiG-21's SPRD-99 rocket boosters during a rocket-assisted takeoff.
- **Wings Fold/Unfold** — vibration while carrier-aircraft wings fold or unfold.
- **Thrust Reverser** — vibration while thrust reversers deploy and stay engaged on landing rollout.
- **Compressor Stall** — a sharp jolt from a jet engine compressor stall.
- **Gear/Structural Turbulence** — extra airframe turbulence felt with the landing gear extended.
- **Slats Movement** — vibration while the leading-edge slats are in transit; has its own Movement filter parameter.

### Combat effects

- **Cannon/Gun Fire** — vibration from firing cannon or machine guns.
- **Payload Release/Missile Launch** — vibration when ordnance leaves a pylon.
- **Chaff/Flare Dispense** — vibration when chaff or flares are dispensed.

### Damage effects

- **Failure and Damage** — vibration when the aircraft takes a hit or suffers a system failure.

### Misc effects

- **Sound: Crew Voices** — on multi-crew helicopters, plays a crew-voice warning (for example the second pilot or flight engineer calling out a high vertical speed) — a sound-only effect.
- **G-Force Effect** — vibration tied to felt G load, with configurable positive/negative deadzones and toggles to ignore roll-induced G, stay active on the ground, or turn off entirely while airborne.
- **Turbulence** — vibration from atmospheric turbulence and strong wind; see the [turbulence editor](#turbulence) for how it's tuned.
- **Effective Translational Lift (ETL)** — the shudder a helicopter feels transitioning into forward flight, as it moves out of its own rotor downwash.
- **Hover Buffet** — vibration felt while a helicopter hovers, from rotor-wash turbulence around the airframe.
- **Refueling Probe/Door** — vibration while a refueling probe or door is moving.
- **Tail Hook** — vibration when the arrestor hook releases or stows.
- **LaunchBar** — vibration while a carrier aircraft's catapult launch bar extends or retracts.
- **Direct Lift Control** — vibration when the direct lift control system is actuated (used on some attack aircraft to adjust lift without pitching).
- **Catapult Shoot** — the kick of a carrier catapult launch.
- **Wire Trap** — the jolt of an arrestor wire catching the aircraft on landing.
- **Bomb Bay Door** — vibration while bomb bay doors open or close.

For more on how any of these effects gets to your hardware, see [Output Devices](devices.html).
