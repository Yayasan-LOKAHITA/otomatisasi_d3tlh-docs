# Habitat and Biodiversity Supporting Ecosystem Service Index (IJLH_PHK)

## Description

This algorithm is used to calculate the **Habitat and Biodiversity Supporting Ecosystem Service Index (IJLH_PHK)** based on specific spatial parameters in Indonesia.

The methodology is based on the **D3TLH Technical Guideline 2024** and has been adapted to support spatial analysis at both national and island scales.

---

## Purpose

To assess the level of ecosystem support for biodiversity conservation through spatial analysis of land cover, vegetation characteristics, and ecoregions.

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

### 4. Special Criteria (Kriteria Khusus / KK) Dataset

Download the Kriteria Khusus dataset from:

[Download Here](https://1drv.ms/f/c/0192f2f41be57bd4/IgCw7lvsknN3QJTTjA-p8XEuAQe9-eJ6gY4RFqZVkMnLekk?e=aEwdG4)

---

## Output

- Vector map containing the **Habitat and Biodiversity Supporting Ecosystem Service Index (IJLH_PHK)** values.

---

## Methodology

The index is calculated using a scoring and weighting approach that integrates:

- Land Cover characteristics (`PL`)
- Ecoregion landform characteristics (`KBA_250`)
- Ecoregion vegetation characteristics (`KVA_250`)

Scores are assigned according to ecological criteria and combined to generate the final index value.

---

## Example Workflow

1. Select the study area scale (**National** or **Island**).

   > If using an island-scale analysis, ensure that the Land Cover dataset contains a `PULAU` field.

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

## References

- D3TLH Technical Guideline 2024
- D3TLH Technical Guideline 2025

---

## Notes

> It is recommended **not to save the output as a temporary layer** to avoid data loss and improve workflow reproducibility.

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