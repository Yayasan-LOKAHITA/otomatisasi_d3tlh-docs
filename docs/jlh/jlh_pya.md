# Water Provision Ecosystem Service Index (JLH_PYA)

## Overview

This algorithm calculates the **Water Provision Ecosystem Service Index (JLH_PYA)**, which represents an ecosystem's ability to provide, store, and maintain the availability of surface water and groundwater resources.

The methodology is based on the **D3TLH Technical Guideline 2024** and has been adapted for spatial analysis across Indonesia at both national and island scales.

---

## Purpose

To assess the capacity of ecosystems to support water availability through spatial analysis of land cover and ecoregion characteristics that influence water infiltration, storage, and retention processes.

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

- Vector map containing the **Water Provision Ecosystem Service Index (JLH_PYA)** values.

---

## Methodology

The index is calculated using a scoring and weighting approach based on the interaction between:

- Land Cover characteristics (`PL`)
- Ecoregion landform characteristics (`KBA_250`)
- Ecoregion vegetation characteristics (`KVA_250`)

These parameters influence ecosystem functions related to:

- Water infiltration
- Groundwater recharge
- Surface water retention
- Water storage capacity
- Long-term water availability

The combined scores are weighted and integrated to produce the final JLH_PYA value.

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

Produces JLH_PYA values for each polygon feature resulting from the analysis.

### Grid Output

Produces JLH_PYA values aggregated to the specified grid system.

---

## Interpretation

Higher index values indicate ecosystems with greater capacity to:

- Store water resources
- Support groundwater recharge
- Maintain surface water availability
- Regulate hydrological processes
- Sustain long-term water supply

Lower index values indicate ecosystems with limited capacity to retain and provide water resources.

---

## Applications

The resulting index can be used for:

- Water resource planning
- Watershed management
- Ecosystem service assessment
- Environmental carrying capacity analysis
- Regional environmental reporting
- D3TLH environmental quality assessments

---

## Notes

- For island-scale analysis, ensure the Land Cover layer contains a valid `PULAU` field.
- The Grid layer is mandatory when selecting Grid output.
- It is recommended to save the output as a permanent layer rather than a temporary layer.
- Ensure that all required fields are properly standardized before running the analysis.
- The accuracy of the index depends on the quality and consistency of the input land cover and ecoregion datasets.

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