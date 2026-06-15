# Carbon Sequestration and Storage Ecosystem Service Index (JLH_PPK)

## Overview

This algorithm calculates the **Carbon Sequestration and Storage Ecosystem Service Index (JLH_PPK)**, which represents an ecosystem's ability to absorb, store, and retain atmospheric carbon.

The methodology follows the **D3TLH Technical Guideline 2024** and has been adapted to Indonesia's ecological and spatial conditions for analysis at both national and island scales.

---

## Purpose

To assess the capacity of ecosystems to support climate change mitigation through ecosystem functions related to carbon sequestration and storage.

The index evaluates ecosystem contributions through:

- Carbon uptake by natural vegetation and cultivated landscapes.
- Carbon storage in aboveground and belowground biomass.
- Carbon retention within soil systems.
- Ecological processes that help reduce greenhouse gas concentrations in the atmosphere.

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

- Vector map containing the **Carbon Sequestration and Storage Ecosystem Service Index (JLH_PPK)** values.

---

## Methodology

The index is calculated using a **scoring and weighting approach** that combines:

- Land Cover characteristics (`PL`)
- Ecoregion landform characteristics (`KBA_250`)
- Ecoregion vegetation characteristics (`KVA_250`)

Land cover classes with high biomass density, such as:

- Natural forests
- Mangrove forests
- Peatland vegetation
- Dense woody vegetation

receive higher scores due to their greater carbon sequestration and storage potential.

Additional weighting is applied based on ecoregion characteristics that influence:

- Biomass productivity
- Carbon accumulation capacity
- Long-term carbon retention

The integrated scores are combined to generate the final JLH_PPK value.

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

Produces JLH_PPK values for each polygon feature resulting from the analysis.

### Grid Output

Produces JLH_PPK values aggregated to the specified grid system.

---

## Interpretation

Higher index values indicate ecosystems with greater capacity to:

- Sequester atmospheric carbon.
- Store carbon in vegetation biomass.
- Retain carbon within soil systems.
- Contribute to climate change mitigation.
- Reduce net greenhouse gas emissions.

Lower index values indicate ecosystems with limited carbon sequestration and storage capacity.

---

## Applications

The resulting index can be used for:

- Climate change mitigation assessments
- Carbon stock and carbon sink analysis
- Ecosystem service valuation
- Environmental carrying capacity assessments
- Regional environmental planning
- Land-use management and conservation planning
- D3TLH environmental quality assessments

---

## Notes

- For island-scale analysis, ensure the Land Cover layer contains a valid `PULAU` field.
- The Grid layer is mandatory when selecting Grid output.
- It is recommended to save the output as a permanent layer rather than a temporary layer.
- Ensure that all required fields are properly standardized before running the analysis.
- Land cover classes with high biomass generally contribute more significantly to the final index value.
- The quality of the resulting index depends on the accuracy and consistency of the Land Cover and Ecoregion datasets.

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