# Product requirements — draft v0.1

## Product goal
Affordable, reproducible, contactless bedside heart-rate and respiration-rate monitoring research platform, packaged with its own sensor, hub, sirens and caregiver UI.

## Functional requirements
- PR-001: Capture radar data and report HR, RR, measurement quality, and timestamps separately.
- PR-002: Report no-target, motion/poor signal, sensor fault and connectivity fault distinctly.
- PR-003: Operate bedside measurement and local hub without cloud dependency.
- PR-004: Support supervised local household alarm-test delivery, acknowledgment and logs.
- PR-005: Present live and historical readings via accessible local web UI.
- PR-006: Store local event history; provide opt-in caregiver access.
- PR-007: Provide firmware version, diagnostics, battery/power and link health.
- PR-008: Include all required product hardware; no dependency on an existing personal PC.
- PR-009: Publish editable sources and neutral manufacturing exports.
- PR-010: Provide synthetic simulation mode visibly separated from real sensor data.

## Nonfunctional requirements
- NR-001: Cost optimized with published costed BOM and alternatives.
- NR-002: Authenticated pairing and communications; signed update design.
- NR-003: Fault handling must not silently substitute old measurements for current readings.
- NR-004: Traceability from risks to requirements and verification results.
- NR-005: Usable by people with impaired vision/hearing and nontechnical caregivers.

## Explicit exclusions until validated
- No diagnosis of myocardial infarction, cardiac arrest, arrhythmia or apnea.
- No promise of life-saving alarms or guaranteed phone notification delivery.
- No automatic emergency dispatch.
- No marketing as a certified medical device.

## Verification
Each requirement will receive a test ID, acceptance criteria and recorded evidence. Numerical accuracy/latency thresholds remain provisional until clinical intended use and reference test plan are approved.
