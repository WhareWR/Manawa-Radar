# System architecture (proposal)

```text
[60 GHz FMCW bedside sensor]
  | radar frames -> range/phase DSP -> HR/RR estimates + measurement quality
  | independent processor supervision and local fault indication
  v
[Dedicated home hub] <----> [Battery-backed, supervised household sirens]
  | local history / fault routing / event log
  +----> [Local web dashboard]
  +----> [Optional LTE/internet gateway] ---> [Caregiver Flutter app]
```

## Design priorities

1. No reliance on a user's existing computer or cloud service for local operation.
2. Minimize parts count and recurring cost without weakening validated safety requirements.
3. Measurement state must distinguish VALID, MOTION_ARTIFACT, NO_TARGET, SENSOR_FAULT, LINK_FAULT, and INITIALIZING.
4. A fault or missing measurement is **not** a cardiac event.
5. Use authenticated device identity, signed firmware, encrypted links, and local-first storage.
6. Record timestamps, device version, algorithm version, signal quality, and alert delivery/acknowledgement status.
7. Alarm test functions must be clearly distinguishable from medical alarms.
8. Formal emergency thresholds, alarm latency, performance claims, and fail-safe behavior remain undefined until risk assessment and clinical validation.

## Initial hardware candidates

- Infineon BGT60TR13C FMCW radar evaluation platform for acquisition feasibility.
- MCU with measured headroom for DSP, memory, watchdog and communication workloads.
- Independent hardware supervisor.
- Dedicated hub with local radio and optional certified LTE module.
- Battery-backed wireless sirens.

No specific PCB, antenna stack-up, power budget or production BOM is approved yet.

## UI

A shared Flutter codebase may target Android, iOS and local web. Required screens: onboarding, monitoring, trends, technical faults, alert tests, caregivers, settings and device diagnostics. All synthetic readings must be labeled as simulated.

## Engineering gate

Do not select a custom radar PCB or advertise life-saving detection until representative sleep-position recordings and reference ECG/respiratory comparisons support feasibility.
