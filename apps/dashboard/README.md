# Manawa-Radar dashboard — runnable simulated UI

Svelte 5 + TypeScript + Vite. This is a **research UI prototype** with synthetic measurements; no real device integration, siren activation, or medical-event detection.

## Run

Requirements: Node.js 20.19+ or 22.12+ and npm.

```sh
cd apps/dashboard
npm install
npm run dev
```

Open the local URL printed by Vite (normally http://127.0.0.1:5173).

```sh
npm run check
npm run build
```

## Available features

- Responsive dashboard with simulated heart/respiration/quality values.
- Live synthetic trend.
- Simulated sensor-state selector; no stale HR/RR displayed on invalid state.
- Simulated technical-alert test and in-memory event log.
- Explicit unconnected device inventory.

## Next

Implement authenticated local hub API, persistent SQLite event history, validated signal-quality states, accessibility tests, and hardware-in-the-loop alarm tests. Never treat this simulation as a patient monitor.
