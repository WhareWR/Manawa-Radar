# Applications — proposed lightweight stack

**Web dashboard:** Svelte + TypeScript, statically built and served by the local hub.

**Mobile:** Capacitor + Svelte + TypeScript with explicit native integration tests for Android/iOS notifications and background operation.

**Shared:** TypeScript event schemas, API client, accessible components, simulation fixtures.

## Principles
- No Flutter/Dart dependency.
- No mandatory Google cloud, hosted account or remote backend for local monitoring.
- Embedded safety monitoring and siren activation must never depend on the UI or phone app.
- Distinguish VALID, UNAVAILABLE, TECHNICAL_FAULT, SIMULATED_TEST and any future clinically validated alarm.
- Mobile notifications are supplementary and subject to OS/network delivery limitations.
- Verify app lifecycle, accessibility, battery behavior, offline operation and real-device alarm workflows before release.

This is a technology selection, not an implemented application.
