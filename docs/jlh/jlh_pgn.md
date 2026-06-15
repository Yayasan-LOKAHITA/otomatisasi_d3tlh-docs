# Food Provision Ecosystem Service Index (JLH_PGN)

## Overview

This algorithm calculates the **Food Provision Ecosystem Service Index (JLH_PGN)**, which represents an ecosystem's capacity to provide food resources from both natural ecosystems and cultivated production systems.

The methodology follows the **D3TLH Technical Guideline 2024** and has been adapted to Indonesia's ecological and ecoregional conditions for analysis at both national and island scales.

---

## Purpose

To assess the capacity of ecosystems to provide food provisioning services through spatial analysis of land cover and ecoregion characteristics.

The index evaluates ecosystem functions that support:

- Natural food resources derived from forests, wetlands, rivers, lakes, and coastal ecosystems.
- Agricultural production systems, including croplands and plantations.
- Aquaculture and fisheries production.
- Ecological processes that contribute to local and regional food security.

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

- Vector map containing the **Food Provision Ecosystem Service Index (JLH_PGN)** values.

---

## Methodology

The index is calculated using a **scoring and weighting approach** that combines:

- Land Cover characteristics (`PL`)
- Ecoregion landform characteristics (`KBA_250`)
- Ecoregion vegetation characteristics (`KVA_250`)

The integrated scores reflect the ecosystem's ability to:

- Provide natural food resources.
- Support agricultural productivity.
- Support fisheries and aquaculture production.
- Maintain ecological functions that contribute to food resilience and food security.

The weighted combination of these parameters produces the final JLH_PGN value.

---

## Processing Workflow

1. Select the study area scale (**National** or **Island**).

   > If using island-scale analysis, the Land Cover dataset must contain a `PULAU` field.

2. Select the output type:

   - Polygon
   - Grid

3. If **Grid** output is selected, provide a Grid layer generated using the Utility module.

4. Provide the required datasets:

   - Land Cover (`PL`)
   - Ecoregion (`KBA_250`, `KVA_250`)

5. (Optional) Provide a Grid layer for grid-based analysis.

6. Run the algorithm.

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

Produces JLH_PGN values for each polygon feature resulting from the analysis.

### Grid Output

Produces JLH_PGN values aggregated to the specified grid system.

---

## Interpretation

Higher index values indicate ecosystems with greater capacity to:

- Produce food resources.
- Support agricultural and plantation productivity.
- Sustain fisheries and aquaculture activities.
- Maintain ecological functions that contribute to food security.

Lower index values indicate ecosystems with reduced capacity to provide food resources and support long-term food production.

---

## Applications

The resulting index can be used for:

- Food security assessments
- Environmental carrying capacity analysis
- Ecosystem service valuation
- Regional development planning
- Sustainable agriculture and fisheries management
- D3TLH environmental quality assessments

---

## Notes

- For island-scale analysis, ensure the Land Cover layer contains a valid `PULAU` field.
- The Grid layer is mandatory when selecting Grid output.
- It is recommended to save the output as a permanent layer rather than a temporary layer.
- Ensure that all required fields are properly standardized before running the analysis.
- The quality of the resulting index depends on the accuracy of the Land Cover and Ecoregion datasets.

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