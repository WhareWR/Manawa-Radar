# Manawa-Radar

**Affordable, open-source, contactless heart-rate and respiratory-rate monitoring research.**

[Dashboard](apps/dashboard/README.md) · [Architecture](docs/ARCHITECTURE.md) · [Requirements](docs/PRODUCT_REQUIREMENTS.md) · [Roadmap](docs/ROADMAP.md) · [Questions](QUESTIONS.md) · [Candidate BOM](hardware/bom/candidate-bom.csv) · [File formats](docs/FILE_ARCHITECTURE.md)

> **RESEARCH / PRECLINICAL — NOT A MEDICAL DEVICE.** The current dashboard displays **synthetic data only**. It is not connected to a radar, cannot detect cardiac arrest, and must not be used for patient care or emergency monitoring.

## Vision

A standalone packaged bedside 60 GHz radar sensor, local hub, supervised battery-backed household sirens and caregiver interfaces, designed to minimize manufacturing cost and cloud dependencies. The long-term aim is medical-grade engineering supported by independent clinical and regulatory evidence—not an assertion of present certification.

## What's implemented

- Runnable responsive **Svelte + TypeScript** research dashboard with simulated HR/RR, quality and fault states, synthetic trends and alarm-test log.
- Versioned JSON Schema for telemetry events.
- Vendor-neutral hardware deliverable conventions, CAD provenance register and provisional costed BOM.
- Initial product requirements, system architecture, roadmap, contribution/security guidance and a dedicated questions/blockers file.

## Run the UI

Requires Node.js 20.19+ or 22.12+.

```bash
cd apps/dashboard
npm install
npm run dev
```

The dashboard is local-only and currently uses simulated data. Build and static checks: `npm run check && npm run build`. **These commands have not yet been verified in CI.**

## Planned components

- **Sensor:** raw-IQ-capable FMCW radar, embedded C/C++ DSP, measurement quality, supervision.
- **Hub:** local API/event storage, independent alarm supervision, optional cellular SKU.
- **Sirens:** supervised wireless, backup power, test/acknowledgement.
- **Interfaces:** Svelte dashboard and future Capacitor mobile shell, subject to native notification reliability testing.
- **Open hardware:** editable CAD in any supported tool; Gerber X2/Excellon, BOM/placement CSV, STEP, STL/3MF, DXF and PDF outputs as appropriate.
- **Verification:** ECG/respiration reference comparison, RF/radome testing, power/network failure testing and clinical/regulatory assessment.

## Affordability

Initial **unverified** engineering target: CAD 140–250 manufacturing cost per kit at volume; this is not a supplier quote and excludes some certification, support and distribution costs. See [candidate BOM](hardware/bom/candidate-bom.csv).

## Design rules

1. Local monitoring and fault indication must not rely on a phone app or cloud.
2. Measurement loss is not evidence of a medical emergency.
3. Never present stale data as current or simulated data as patient measurements.
4. Document unanswered design decisions in [QUESTIONS.md](QUESTIONS.md), continue independent work.
5. Keep original editable CAD sources and neutral fabrication outputs; verify third-party model licences.

## Licensing

**Not yet finalized:** proposed Apache-2.0 (software), CERN-OHL-S-2.0 (hardware), CC-BY-4.0 (documentation). Do not assume these are already granted; licence files and contributor agreement remain open questions.
