# Flood Regulation Ecosystem Service Index (IJLH_PGA)

## Overview

This algorithm calculates the **Flood Regulation Ecosystem Service Index (IJLH_PGA)**, which represents an ecosystem's ability to regulate surface water flow, reduce runoff, and prevent flooding or waterlogging.

The methodology is based on the **D3TLH Technical Guideline 2024** and has been adapted for spatial analysis across Indonesia at both national and island scales.

---

## Purpose

To assess the ecosystem's capacity to control flooding and surface water accumulation through spatial analysis of land cover and ecoregion characteristics that influence water infiltration, retention, and flow regulation.

---

## Required Inputs

### 1. Land Cover Map

Vector dataset containing the following field:

- `PL`

### 2. Ecoregion Map

Vector dataset containing the following fields:

- `KBA_250`
- `KVA_250`

### 3. Study Area Grid Layer (Optional)

Required only when the selected output type is **Grid**.

---

## Output

The algorithm generates:

- Vector map containing the **Flood Regulation Ecosystem Service Index (IJLH_PGA)** values.

---

## Methodology

The index is calculated using a **scoring and weighting approach** that combines:

- Land Cover characteristics (`PL`)
- Ecoregion landform characteristics (`KBA_250`)
- Ecoregion vegetation characteristics (`KVA_250`)

The resulting scores represent the ecosystem's ability to:

- Reduce surface runoff
- Regulate water flow
- Increase water infiltration
- Lower the risk of flooding and waterlogging

The weighted scores are integrated to produce the final IJLH_PGA value.

---

## Processing Workflow

1. Select the study area scale (**National** or **Island**).

   > If using island-scale analysis, the Land Cover dataset must contain a `PULAU` field.

2. Select the output type:

   - Polygon
   - Grid

3. If **Grid** output is selected, provide a Grid layer generated using the Utility module.

4. Specify the year of the Land Cover dataset.

5. Provide the required datasets:

   - Land Cover (`PL`)
   - Ecoregion (`KBA_250`, `KVA_250`)

6. (Optional) Provide a Grid layer for grid-based analysis.

7. Run the algorithm.

---

## Input Requirements

### Land Cover Layer

The input layer must contain:

| Field | Description |
|---------|-------------|
| `PL` | Land Cover classification |

### Ecoregion Layer

The input layer must contain:

| Field | Description |
|---------|-------------|
| `KBA_250` | Ecoregion Landform Characteristic |
| `KVA_250` | Ecoregion Natural Vegetation Characteristic |

### Grid Layer (Optional)

Required when generating grid-based outputs.

The grid can be generated using the **Utility → IMGS/Grid Generation** module.

---

## Output Types

### Polygon Output

Produces IJLH_PGA values for each polygon feature resulting from the analysis.

### Grid Output

Produces IJLH_PGA values aggregated to the specified grid system.

---

## Interpretation

Higher index values indicate ecosystems with greater capacity to:

- Regulate surface water flow
- Reduce runoff
- Increase water retention
- Mitigate flooding and waterlogging

Lower index values indicate ecosystems with limited flood regulation capacity and lower effectiveness in controlling surface water accumulation.

---

## Notes

- For island-scale analysis, ensure the Land Cover layer contains a valid `PULAU` field.
- The Grid layer is mandatory when selecting Grid output.
- It is recommended to save the output as a permanent layer rather than a temporary layer.
- Ensure that all required fields are properly standardized before running the analysis.

---

## References

- D3TLH Technical Guideline 2024
- D3TLH Technical Guideline 2025

---

## Author

**Yayasan Lokahita**

- Fadillah Azhar Deaudin Kurniawan
- Sitarani Safitri
- Dini Aprilia Norvyani
- Suchi Rahmadani
- Fariz Rizaldy Wibowo

### Supported By
Directorate for Environmental Impact Prevention and Regional Sectoral Policy  
Kementerian Lingkungan Hidup Republik Indonesia