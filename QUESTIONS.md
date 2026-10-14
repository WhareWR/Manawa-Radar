# Open questions and decisions

Questions are tracked here instead of silently blocking unrelated work. **BLOCKED** means a specific subsystem must not be finalized until answered; work on other subsystems continues.

| ID | Priority | Question | Default / next action | Blocks |
|---|---|---|---|---|
| Q-001 | BLOCKED | What exact clinical intended use and patient population are in scope? HR/RR trending only, or emergency detection? | Start as **research-only HR/RR estimation**, no clinical alarm claim. Consult clinician/regulatory specialist. | Medical alarm logic, marketing, clinical study endpoints |
| Q-002 | BLOCKED | What measurement distance, bed geometry, number of occupants, and mounting location? | Build adjustable test jig; collect representative recordings. | RF antenna/radome design, final enclosure |
| Q-003 | BLOCKED | Which radar chip/module gives raw phase/IQ access at production volumes, with supported SDK and supply? | Evaluate Infineon BGT60TR13C and TI alternatives; measure before selection. | Production PCB and firmware drivers |
| Q-004 | BLOCKED | Which jurisdictions and regulatory pathway are targeted first? | Research prototype only; begin Canadian classification assessment. | Clinical claims, compliance plan |
| Q-005 | HIGH | What is the maximum landed manufacturing cost and intended retail price? | Working targets: CAD 140–250 kit COGS, retail CAD 299–399; **unverified**. | Production trade-offs |
| Q-006 | HIGH | Must the kit include cellular hardware and service, or is cellular an optional SKU? | Make LTE optional; local hub/siren independent of cloud. | Hub SKU/BOM |
| Q-007 | HIGH | How many sirens, minimum runtime during outage, and required sound pressure? | Prototype with 2 sirens; verify accessibility and IEC alarm requirements. | Power budget and siren PCB |
| Q-008 | HIGH | What open-hardware/software licence policy should govern contributions? | Propose CERN-OHL-S-2.0 for hardware, Apache-2.0 software, CC-BY-4.0 docs; **not yet licensed**. | Redistribution of third-party models |
| Q-009 | MEDIUM | Preferred PCB assembly/fabrication regions and supply-chain constraints? | Keep vendor-neutral manufacturing exports. | Supplier-qualified BOM |
| Q-010 | MEDIUM | Should local web dashboard be available without accounts, or require device pairing/authentication? | Require authenticated pairing for sensitive measurements. | Identity implementation |
| Q-011 | MEDIUM | What caregiver languages and accessibility requirements are needed? | English first with localization architecture; Māori support planned. | Final copy/localization |
| Q-012 | MEDIUM | Do we need wall mounting, bedside stand, or both? | Design interchangeable mounting geometry after RF tests. | Final enclosure |
| Q-013 | MEDIUM | Should optional mobile apps use Capacitor or fully native shells after reliability tests? | Build responsive Svelte dashboard first; test mobile background delivery separately. | Mobile release |

## Working rule

Proceed with non-blocked software, UI, schema, test fixtures, documentation, research tooling, and vendor-neutral mechanical/electrical interfaces. Never turn an unanswered clinical question into an unvalidated safety assumption.
