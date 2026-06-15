# Biodiversity Utilization Capability Index (IKP Kehati)

## Overview

This module calculates the **Biodiversity Utilization Capability Index (IKP Kehati)**, an indicator used to assess the capacity of biodiversity resources to support ecosystem functions, ecosystem services, and sustainable human activities.

The methodology integrates biodiversity-supporting environmental components, including land cover, habitat conditions, ecoregions, protected areas, important biodiversity areas, water resources, and population distribution.

The resulting index provides a spatial representation of biodiversity utilization pressure and ecosystem support capacity, supporting environmental carrying capacity assessments, conservation planning, and D3TLH workflows.

---

## Purpose

To evaluate the capacity of biodiversity resources in supporting ecological processes and human well-being by integrating biodiversity-related indicators into a standardized index.

The analysis produces:

* Biodiversity Utilization Capability Index (IKP Kehati)
* Biodiversity Capability Classification
* Biodiversity Capability Score
* Grid-based biodiversity assessment
* Polygon-based biodiversity assessment

---

## Required Inputs

### 1. IJLH PKU Layer

Vector dataset representing biodiversity protection and conservation components.

### 2. IJLH PGA Layer

Vector dataset representing biodiversity ecosystem service components.

### 3. IJLH PPK Layer

Vector dataset representing biodiversity preservation and ecological support components.

### 4. IJLH PYA Layer

Vector dataset representing biodiversity-related water resource components.

### 5. Land Cover Layer (PL)

Land cover dataset used to evaluate habitat condition and ecosystem quality.

Required field:

* `PL`

### 6. Ecoregion Layer

Vector dataset representing ecological regions.

### 7. RTE Layer

Vector dataset containing Rare, Threatened, and Endangered (RTE) species information.

### 8. Habitat Layer

Vector dataset representing habitat distribution and biodiversity-supporting ecosystems.

### 9. Population Grid Layer

Grid-based population distribution dataset.

Required field:

* `POPGRIDYY`

### Sample Data

Ecoregion, RTE, and Habitat datasets can be downloaded from:

[Download Here](https://1drv.ms/f/c/0192f2f41be57bd4/IgCrBpWOqxvaTIzz8gqsefHUAX5hU69vv9VZuguUZaD0K3I?e=wLMnjS)

---

## Output

The algorithm produces:

### 1. Biodiversity IKP Polygon Layer

Spatial biodiversity assessment aggregated into polygon units.

### 2. Biodiversity IKP Grid Layer

Grid-based biodiversity assessment.

Each grid contains:

| Field        | Description                               |
| ------------ | ----------------------------------------- |
| `ID`         | Grid identifier                           |
| `IKP_KEHATI` | Biodiversity Utilization Capability Index |
| `KELAS_IKP`  | IKP classification                        |
| `SKOR_IKP`   | IKP score                                 |
| `PKU`        | Biodiversity protection component         |
| `PGA`        | Biodiversity ecosystem service component  |
| `PPK`        | Biodiversity preservation component       |
| `PYA`        | Biodiversity water resource component     |

---

## Methodology

The Biodiversity IKP is derived by integrating multiple biodiversity-supporting indicators.

### Biodiversity Protection Component (PKU)

The PKU dataset is intersected with the analysis grid to calculate biodiversity protection values.

Output field:

```text
PKU
```

---

### Biodiversity Ecosystem Service Component (PGA)

The PGA dataset is intersected with the analysis grid to calculate ecosystem service support values.

Output field:

```text
PGA
```

---

### Biodiversity Preservation Component (PPK)

The PPK dataset is intersected with the analysis grid to calculate biodiversity preservation values.

Output field:

```text
PPK
```

---

### Biodiversity Water Resource Component (PYA)

The PYA dataset is intersected with the analysis grid to calculate biodiversity-related water resource values.

Output field:

```text
PYA
```

---

### Habitat Assessment

Habitat quality and habitat extent are evaluated within each analysis grid.

Factors considered include:

* Habitat availability
* Habitat continuity
* Habitat suitability
* Habitat fragmentation

---

### Ecoregion Assessment

Ecoregion characteristics are used to account for ecological variability and regional biodiversity potential.

---

### RTE Assessment

Rare, Threatened, and Endangered species distributions are incorporated to represent biodiversity significance and conservation value.

---

### Composite Biodiversity Score

The biodiversity components are standardized and combined into a composite biodiversity index.

Conceptually:

```text
IKP_KEHATI = f(PKU, PGA, PPK, PYA, Habitat, Ecoregion, RTE)
```

where:

* `PKU` = Biodiversity protection component
* `PGA` = Ecosystem service component
* `PPK` = Biodiversity preservation component
* `PYA` = Water resource component
* `Habitat` = Habitat quality indicator
* `Ecoregion` = Ecological region indicator
* `RTE` = Rare, Threatened, and Endangered species indicator

---

### Classification

The resulting IKP values are classified into five categories.

| Score | Class     |
| ----- | --------- |
| 5     | Very High |
| 4     | High      |
| 3     | Moderate  |
| 2     | Low       |
| 1     | Very Low  |

Output fields:

```text
KELAS_IKP
```

```text
SKOR_IKP
```

---

## Processing Workflow

1. Harmonize the coordinate reference system (CRS) of all datasets.
2. Repair invalid geometries and create spatial indexes.
3. Load:

   * IJLH PKU
   * IJLH PGA
   * IJLH PPK
   * IJLH PYA
   * Land Cover
   * Ecoregion
   * RTE
   * Habitat
   * Population Grid
4. Standardize input fields and geometries.
5. Intersect biodiversity datasets with the analysis grid.
6. Calculate:

   * PKU
   * PGA
   * PPK
   * PYA
7. Evaluate habitat conditions.
8. Evaluate ecoregion characteristics.
9. Evaluate RTE significance.
10. Standardize component values.
11. Calculate:

    * IKP_KEHATI
12. Classify biodiversity capability into:

    * Very High
    * High
    * Moderate
    * Low
    * Very Low
13. Assign:

    * KELAS_IKP
    * SKOR_IKP
14. Generate polygon outputs.
15. Generate grid outputs.

---

## Output Interpretation

### High IKP Values

Indicate:

* Healthy biodiversity conditions
* Strong ecosystem functionality
* High ecological resilience
* Significant ecosystem service provision
* Strong biodiversity support capacity

### Moderate IKP Values

Indicate:

* Biodiversity resources remain functional
* Some ecological pressure may exist
* Management interventions may be beneficial

### Low IKP Values

Indicate:

* Biodiversity degradation
* Reduced ecosystem services
* Habitat fragmentation
* Increased ecological pressure
* Higher conservation priority

### High SKOR_IKP

Indicates areas with strong biodiversity support and ecological sustainability.

### Low SKOR_IKP

Indicates areas requiring biodiversity conservation and ecosystem restoration efforts.

---

## Applications

The resulting Biodiversity IKP dataset can be used for:

* Environmental Carrying Capacity (DDLH) analysis
* Biodiversity assessment
* Conservation planning
* Ecosystem service evaluation
* Ecological restoration prioritization
* Spatial planning
* Sustainable development assessment
* Environmental policy development
* D3TLH analysis workflows

---

## Notes

* All input layers should use the same CRS.
* Habitat, ecoregion, and RTE datasets should be spatially consistent.
* Biodiversity assessments are sensitive to land cover quality and habitat conditions.
* Population distribution may influence biodiversity utilization pressure.
* It is recommended not to save outputs as temporary layers.
* The quality of the results depends on the completeness and accuracy of biodiversity-related datasets.

---

## Author

**Yayasan Lokahita**

* Fadillah Azhar Deaudin Kurniawan
* Sitarani Safitri
* Dini Aprilia Norvyani
* Suchi Rahmadani
* Fariz Rizaldy Wibowo

### Supported By
Directorate for Environmental Impact Prevention and Regional Sectoral Policy  
Kementerian Lingkungan Hidup Republik Indonesia
