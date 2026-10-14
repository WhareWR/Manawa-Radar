# Manawa-Radar

**Affordable, open-source, contactless cardiac and respiratory monitoring research.**

Manawa-Radar aims to develop a reproducible, standalone bedside monitoring product with a 60 GHz radar sensor, local hub, household sirens, and caregiver mobile/web interfaces. The project prioritizes accessible hardware, privacy, offline operation, and a rigorous pathway to medical-device quality.

> **Safety status: RESEARCH / PRECLINICAL.** No implementation in this repository is a certified medical device, validated cardiac-arrest detector, or replacement for ECG monitoring, emergency services, or prescribed medical equipment. Loss of radar heartbeat tracking does not establish cardiac arrest. No emergency alarm claims are authorized without clinical validation and applicable regulatory clearance.

## Product components

- **Bedside sensor:** FMCW radar, local DSP, signal quality, secure communications, device supervision.
- **Home hub:** offline-first event routing, technical-fault reporting, siren supervision, optional cellular failover.
- **Household sirens:** independent power, test/acknowledgment, supervised wireless communications.
- **Mobile app and web UI:** live readings, measurement availability, history, technical faults, caregiver setup, test notifications.
- **Open hardware:** KiCad design sources, enclosure CAD, assembly and calibration guides, BOM and manufacturing tests.
- **Validation:** reproducible ECG/respiration comparisons, motion/sleep-position testing, requirements traceability and risk management.

## First milestones

1. Define intended use, exclusions, measurable requirements and hazard analysis.
2. Reproduce radar acquisition and vital-sign estimates using evaluation hardware; publish reference comparisons and limitations.
3. Prototype a standalone processing board and local communications.
4. Build the shared UI and simulator, with clear **simulated** labels.
5. Verify end-to-end *technical-fault* notifications, alarm-test functionality and power/network failure behavior.
6. Undertake prospective clinical studies and regulatory review before claiming medical emergency detection.

## Repository map

- `docs/` — architecture and product requirements
- `hardware/` — future KiCad, enclosure and BOM source files
- `firmware/` — future sensor, hub and siren firmware
- `algorithms/` — reproducible DSP research
- `apps/` — Flutter mobile and local web interface
- `validation/` — verification and clinical study plans
- `regulatory/` — intended use, hazards, traceability and quality documentation

## Contributing

Contributions are welcome, particularly from radar/DSP engineers, clinicians, accessibility designers and medical-device quality specialists. Do not upload patient-identifiable recordings or confidential medical data.

## Licensing

Licensing is **proposed, not yet finalized**: Apache-2.0 for software, CERN-OHL-S-2.0 for original hardware design files, and CC-BY-4.0 for documentation. Review third-party dependencies and obtain contributor agreement on licensing before copying code or publishing fabrication files. No licence grant is implied until licence texts are added.
