# Indeks Jasa Lingkungan Hidup Pengatur Kualitas Udara (JLH_PKU)

## Overview

This algorithm calculates the **Environmental Ecosystem Service Index for Air Quality Regulation (JLH_PKU)**, which represents the ability of ecosystems to improve and maintain air quality.

The methodology is based on the **D3TLH Technical Guideline 2024** and has been adapted for spatial analysis at both national and island scales.

---

## Purpose

To assess the contribution of ecosystems to air quality improvement through spatial analysis of land cover and ecoregion characteristics that influence the filtration, absorption, and neutralization of air pollutants.

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

- Vector map containing the **Air Quality Regulation Ecosystem Service Index (JLH_PKU)** values.

---

## Methodology

The index is calculated using a scoring and weighting approach based on:

- Land Cover characteristics (`PL`)
- Ecoregion landform characteristics (`KBA_250`)
- Ecoregion vegetation characteristics (`KVA_250`)

Each ecosystem type is assigned a score according to its capacity to:

- Filter airborne pollutants
- Absorb particulate matter
- Sequester atmospheric contaminants
- Improve overall air quality

The weighted scores are then combined to produce the final JLH_PKU value.

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

Produces JLH_PKU values for each polygon feature resulting from the analysis.

### Grid Output

Produces JLH_PKU values aggregated to the specified grid system.

---

## Interpretation

Higher index values indicate ecosystems with greater capacity to:

- Improve air quality
- Filter pollutants
- Support atmospheric regulation functions

Lower index values indicate ecosystems with reduced air quality regulation capacity.

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