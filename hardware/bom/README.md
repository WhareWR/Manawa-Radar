# Recommended BOMs — feasibility stage

See [candidate BOM](candidate-bom.csv). Values are **planning estimates in CAD**, not live vendor quotations or confirmed stock. Costs must be replaced with dated supplier quotations and part numbers before procurement.

## Product variants
1. Sensor: 60 GHz radar + embedded DSP + certified radio + AC adapter + enclosure.
2. Hub: local event processor, wireless siren radio, power backup, optional LTE SKU.
3. Siren: supervised radio, audible/visual indicator, independent power.
4. Complete kit: sensor + hub + 2 sirens + mounting, cables and packaging.

## Selection gates
- Radar must expose adequate raw data for independent algorithm verification; confirm RF certification strategy and sustained component availability.
- Choose processing silicon **after** memory/throughput profiling.
- Battery design needs qualified cells, protection and safety review.
- Choose alarm radio by regional RF regulations, range, coexistence and independent supervision.
- BOM target is not a product guarantee; include assembly yield, calibration, test, warranty and compliance costs.

## Open-hardware policy
Use neutral CAD exports, record alternate parts, and avoid redistribution of third-party library models without licence verification.
