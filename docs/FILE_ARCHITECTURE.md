# Repository and deliverable architecture

```text
Manawa-Radar/
├── README.md                 # Mission, setup, status and safety
├── QUESTIONS.md              # Decisions, blockers and assumptions
├── CONTRIBUTING.md
├── SECURITY.md
├── docs/
│   ├── ARCHITECTURE.md
│   ├── FILE_ARCHITECTURE.md
│   ├── ROADMAP.md
│   └── PRODUCT_REQUIREMENTS.md
├── apps/
│   ├── dashboard/            # Svelte + TypeScript, locally served
│   └── mobile/               # Future native packaging + integration tests
├── packages/
│   └── protocol/             # Versioned JSON schemas / transport contracts
├── services/
│   └── hub/                  # Future hub daemon and event gateway
├── firmware/
│   ├── sensor/
│   ├── hub/
│   └── siren/
├── algorithms/               # DSP research and reproducible notebooks
├── hardware/
│   ├── bom/                  # BOM estimates and approved substitutes
│   ├── sensor/               # CAD source + manufacturing exports
│   ├── hub/
│   ├── siren/
│   ├── enclosure/
│   └── cad-library/
├── validation/               # Bench, reference and clinical protocols
└── regulatory/               # Intended use, hazards, traceability
```

## CAD interoperability contract

**All source formats are welcome:** KiCad, EasyEDA, Altium, Eagle, FreeCAD, SolidWorks, Fusion, Onshape, etc. Each contribution must include original editable files (when redistribution is permitted) and applicable neutral exports.

| Artifact | Required exchange/manufacturing output | Recommended additional output |
|---|---|---|
| PCB fabrication | Gerber X2 + Excellon drill | IPC-2581 |
| PCB assembly | BOM CSV + pick-and-place CSV | Assembly drawing PDF |
| Electrical schematic | PDF | Native EDA project and netlist |
| Parametric mechanical geometry | STEP | Native CAD assembly |
| 3D-printable parts | STL | 3MF |
| Laser-cut panels | DXF | SVG |
| Wiring/harness | PDF diagram + connection table CSV | Native source |
| Firmware | Source + reproducible build instructions | Signed release binary |
| Clinical data | De-identified aggregate metrics and protocol | Restricted-access raw data policy |

Every manufacturing export should include revision, units, tolerances, material, source application/version, and test status. **A file being printable or manufacturable does not imply medical suitability.**

Third-party GrabCAD/OSHWLab/SnapMagic/Flux files must have provenance and verified redistribution permissions; otherwise link to them, do not mirror them.
