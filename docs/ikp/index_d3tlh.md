# D3TLH Index

## Overview

This module calculates the **D3TLH Index (Daya Dukung dan Daya Tampung Lingkungan Hidup)** by integrating the results of environmental carrying capacity assessments from water, land, biodiversity, air, and environmental quality indicators.

The D3TLH Index is a composite environmental index designed to represent the overall condition of environmental carrying capacity and environmental support capacity within a region. It combines multiple environmental dimensions into a single indicator to support environmental planning, monitoring, and policy evaluation.

The resulting index provides a spatially explicit representation of environmental sustainability conditions and can be used as a primary indicator in D3TLH assessments.

---

## Purpose

To evaluate the overall environmental carrying capacity and environmental support capacity of a region through the integration of:

* Water Utilization Capability Index (IKP Air)
* Land Utilization Capability Index (IKP Lahan)
* Biodiversity Utilization Capability Index (IKP Kehati)
* Air Utilization Capability Index (IKP Udara)
* Environmental Quality Preservation Index (IPRLH)

The analysis produces:

* D3TLH Composite Index
* Environmental Sustainability Classification
* Environmental Sustainability Score
* Grid-based D3TLH Assessment

---

## Required Inputs

### 1. Water IKP Layer

Output layer generated from the Water Utilization Capability Index (IKP Air) analysis.

Required field:

* `SKOR_IKP`

### 2. Land IKP Layer

Output layer generated from the Land Utilization Capability Index (IKP Lahan) analysis.

Required field:

* `SKOR_IKP`

### 3. Biodiversity IKP Layer

Output layer generated from the Biodiversity Utilization Capability Index (IKP Kehati) analysis.

Required field:

* `SKOR_IKP`

### 4. Air IKP Layer

Output layer generated from the Air Utilization Capability Index (IKP Udara) analysis.

Required field:

* `SKOR_IKP`

### 5. IPRLH Table

Environmental Quality Preservation Index (IPRLH) table corresponding to the analysis region.

Required fields:

* Administrative identifier
* `IPRLH`

---

## Output

The algorithm produces a **D3TLH Index Layer**.

Each grid contains:

| Field         | Description                              |
| ------------- | ---------------------------------------- |
| `ID`          | Grid identifier                          |
| `IKP_AIR`     | Water IKP score                          |
| `IKP_LAHAN`   | Land IKP score                           |
| `IKP_KEHATI`  | Biodiversity IKP score                   |
| `IKP_UDARA`   | Air IKP score                            |
| `IPRLH`       | Environmental Quality Preservation Index |
| `D3TLH`       | Composite D3TLH Index                    |
| `KELAS_D3TLH` | D3TLH classification                     |
| `SKOR_D3TLH`  | D3TLH score                              |

---

## Methodology

The D3TLH Index is calculated by integrating multiple environmental indicators into a composite environmental sustainability score.

### Water Component

The Water IKP score represents environmental support capacity related to water resources.

Input field:

```text
IKP_AIR
```

---

### Land Component

The Land IKP score represents environmental support capacity related to land resources.

Input field:

```text
IKP_LAHAN
```

---

### Biodiversity Component

The Biodiversity IKP score represents ecological resilience and biodiversity support capacity.

Input field:

```text
IKP_KEHATI
```

---

### Air Component

The Air IKP score represents environmental support capacity related to air quality.

Input field:

```text
IKP_UDARA
```

---

### Environmental Quality Component

The IPRLH indicator represents environmental quality preservation conditions.

Input field:

```text
IPRLH
```

---

### Composite D3TLH Calculation

The D3TLH Index is calculated by combining:

* Water IKP
* Land IKP
* Biodiversity IKP
* Air IKP
* IPRLH

Conceptually:

```text
D3TLH = f(IKP_AIR, IKP_LAHAN, IKP_KEHATI, IKP_UDARA, IPRLH)
```

where:

* `IKP_AIR` = Water capability score
* `IKP_LAHAN` = Land capability score
* `IKP_KEHATI` = Biodiversity capability score
* `IKP_UDARA` = Air capability score
* `IPRLH` = Environmental quality preservation score

The resulting value represents the overall environmental carrying capacity and support capacity condition of the analysis area.

---

### Classification

The resulting D3TLH values are classified into five categories.

| Score | Class     |
| ----- | --------- |
| 5     | Very High |
| 4     | High      |
| 3     | Moderate  |
| 2     | Low       |
| 1     | Very Low  |

Output fields:

```text
KELAS_D3TLH
```

```text
SKOR_D3TLH
```

---

## Processing Workflow

1. Harmonize the coordinate reference system (CRS) of all input layers.
2. Repair invalid geometries and create spatial indexes.
3. Load:

   * Water IKP layer
   * Land IKP layer
   * Biodiversity IKP layer
   * Air IKP layer
   * IPRLH table
4. Verify that all IKP layers contain the required score fields.
5. Standardize grid identifiers across all datasets.
6. Join:

   * Water IKP scores
   * Land IKP scores
   * Biodiversity IKP scores
   * Air IKP scores
7. Join IPRLH values to the analysis grid.
8. Standardize all component scores.
9. Calculate:

   * `D3TLH`
10. Classify D3TLH values into:

    * Very High
    * High
    * Moderate
    * Low
    * Very Low
11. Assign:

    * `KELAS_D3TLH`
    * `SKOR_D3TLH`
12. Generate the final D3TLH Index layer.

---

## Output Interpretation

### High D3TLH Values

Indicate:

* Strong environmental carrying capacity
* High environmental support capacity
* Good environmental quality conditions
* Strong ecosystem resilience
* Sustainable utilization of natural resources

### Moderate D3TLH Values

Indicate:

* Environmental conditions are relatively balanced
* Some environmental pressures may exist
* Continued monitoring and management are recommended

### Low D3TLH Values

Indicate:

* Reduced environmental carrying capacity
* High environmental pressure
* Resource utilization exceeds environmental capacity
* Increased ecological vulnerability
* Priority areas for environmental intervention

### High SKOR_D3TLH

Indicates areas with favorable environmental sustainability conditions and strong ecosystem support capacity.

### Low SKOR_D3TLH

Indicates areas requiring environmental restoration, resource management improvements, and policy intervention.

---

## Applications

The resulting D3TLH Index can be used for:

* D3TLH assessment and reporting
* Environmental carrying capacity evaluation
* Environmental sustainability assessment
* Regional environmental planning
* Environmental monitoring and evaluation
* Strategic environmental assessment
* Sustainable development planning
* Natural resource management
* Environmental policy development

---

## Notes

* All input datasets should use the same CRS.
* All IKP analyses should be completed before running this module.
* The IPRLH table must correspond to the same analysis year as the IKP layers.
* Grid identifiers must be consistent across all input datasets.
* It is recommended not to save outputs as temporary layers.
* The quality of the final D3TLH Index depends on the accuracy of all component indicators.

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