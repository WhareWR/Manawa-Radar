# System architecture (proposal)

```text
[60 GHz FMCW bedside sensor]
  | C/C++ radar acquisition and DSP; measurement-quality states
  | independent processor supervision and local fault indication
  v
[Dedicated local hub: C++/Rust service + SQLite + MQTT]
  | authenticated local API / event routing / technical-fault log
  +----> [Battery-backed supervised wireless sirens]
  +----> [Svelte + TypeScript dashboard, served locally]
  +----> [Optional LTE/internet] ---> [Svelte + Capacitor caregiver app]
```

## Technology selection
- Embedded firmware and production DSP: C/C++.
- Research/validation algorithms: Python + NumPy/SciPy.
- Hub runtime: evaluate C++ vs Rust after resource profiling.
- Web dashboard: Svelte + TypeScript.
- Mobile: Svelte + Capacitor; native notification integrations require physical-device verification.
- Local persistence: SQLite.
- Hardware and mechanical sources: KiCad and FreeCAD.
- No Flutter dependency or mandatory cloud backend.

## Safety invariants
1. A mobile app, web dashboard, cloud service or household Wi-Fi must not be a single point of failure for local technical-fault indication.
2. Distinguish VALID, MOTION_ARTIFACT, NO_TARGET, SENSOR_FAULT, LINK_FAULT and INITIALIZING.
3. Missing heartbeat tracking is **not** evidence of cardiac arrest.
4. Clinical emergency thresholds and alarm claims remain undefined until validation and regulatory authorization.
5. Authenticate devices, sign firmware, supervise alarm units and log device/algorithm versions.
6. Use independent hardware watchdog supervision and safe fault indication.

## Feasibility gate
Validate radar measurements across sleeping positions and motion against ECG/respiratory references before finalizing custom RF PCB or clinical claims.
