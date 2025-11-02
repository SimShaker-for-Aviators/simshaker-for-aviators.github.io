# SimShaker for Aviators Tester (SSA Tester) — Alpha Manual

## 1) What is SSA Tester?
  SSA Tester is a companion diagnostic and analysis tool for SimShaker for Aviators (SSA). It can:
  - Listen to simulator telemetry over UDP/TCP
  - Record sessions to file, replay them (real-time or step-by-step)
  - Visualize signals with plots to tune and debug effects
  - Serve recorded/live data back to an SSA instance for effect testing

  This alpha targets DCS first. MSFS/X-Plane support may appear later.

## 2) Requirements
  - Windows 10/11 x64
  - DCS World (for this guide) and your existing SSA setup
  - Network permissions to receive/send local UDP/TCP traffic (allow through firewall when prompted)

## 3) Quick Start (DCS)
  1. Launch “SimShaker for Aviators Tester” -> In SSA, go to the “View” menu and select SSA Tester” to start the application.
  2. Start DCS World and load any mission.
  3. SSA Tester uses the same ports and protocol that SSA uses with DCS (no manual port configuration in Tester).
  4. You should see packets and plots begin to move (IAS, Mach, TAS, etc.).
  5. Click “Record” to capture data; click “Stop” to finish and save to file.
  6. Use “Replay” to analyze or step through the recorded session.

## 4) UI Tour (at a glance)
  - Connection status (in to bottom menu bar): shows UDP/TCP listener/subscriber state.
  - Packet log: recent packets with timestamps and parsed key/value pairs.
  - Plots: charts of selected metrics.
  - Recorder: Start/Stop, save file.
  - Replayer: Play/Pause, Step (manual mode).
  - Serve mode: exposes a local endpoint so SSA can connect and consume replayed data.

## 5) Core Workflows
  A. Record a live DCS session
   - Ensure packets are arriving (packet counter increases)
   - Click Record, fly your scenario, click Stop, then Save

  B. Replay a recording (local analysis)
   - Open the file, choose playback mode:
     - Auto: press Play and the playback runs automatically
     - Manual: press Step to advance packet by packet

  C. Serve mode: play back to SSA
   - Check “Serve” in SSA Tester to enable its local server endpoint
   - Start SSA (the regular app) and let it connect to the Tester’s endpoint - if SSA is running is should automatically connect to the Tester (it uses the same ports/protocol SSA uses with DCS)
   - Open a recording in Tester and press Play (or Step in Manual); SSA will receive the stream as if it came from the simulator
   - Use this to validate SSA effects without launching DCS

## 6) Connections and Ports
  - SSA Tester uses the same ports and protocol as SSA in combination with DCS
  - Ports are not user-configurable in SSA Tester
  - If packets do not arrive or Serve does not work, verify your SSA/DCS setup and firewall permissions

## 7) Troubleshooting
  - No packets:
    - SSA/DCS not producing data, or firewall blocks local traffic
    - Another tool exclusively bound to the port used by SSA/DCS
  - Serve mode not feeding SSA:
    - Ensure Serve is enabled, SSA is running, and no firewall blocks local connections
    - Do not run multiple tools concurrently that bind the same SSA/DCS ports
  - App starts but no plots:
    - Wait for active telemetry; open a recording and Replay to test visuals

When reporting issues, include Windows version, Tester version, whether packets are received, and (if possible) a short recording that reproduces the problem.
Please use github tickets to repport issues: https://github.com/SimShaker-for-Aviators/SimShaker-for-Aviators-Releases/issues