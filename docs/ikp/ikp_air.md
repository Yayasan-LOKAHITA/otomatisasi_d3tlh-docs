# Water Utilization Capability Index (IKP Air)

## Overview

This module calculates the **Water Utilization Capability Index (IKP Air)**, an indicator used to assess the capability of water resources to support human activities while maintaining environmental sustainability.

The methodology integrates water ecosystem services, river basin water availability, water quality conditions, land-use-based water demand, and population-based water demand. The resulting index represents the balance between available usable water and total water demand within each analysis grid.

The output can be used for environmental carrying capacity assessments, water resource planning, watershed management, and D3TLH analysis workflows.

---

## Purpose

To evaluate the capability of water resources to support human and ecological needs by comparing:

- Available water resources
- Water quality conditions
- Population water demand
- Land-use water demand

The analysis produces:

- Water Utilization Capability Index (IKP Air)
- Water Availability Assessment
- Water Demand Assessment
- Water Capability Classification
- Water Capability Score

---

## Required Inputs

### 1. Analysis Year

Analysis year used to identify year-dependent fields.

| Year | Field Suffix |
|--------|-------------|
| 2024 | `_24` |
| 2025 | `_25` |

---

### 2. JLH Water Provision Grid

Grid layer generated from the **JLH Penyedia Air (PYA)** analysis.

Required field:

```text
PYA_YY_KK
```

where:

- `YY` = last two digits of the analysis year

Example:

```text
PYA_24_KK
```

This field represents water provisioning ecosystem service values.

---

### 3. River Basin Layer (WS)

River basin (Wilayah Sungai) layer.

Required fields:

| Field | Description |
|---------|-------------|
| `WS` | River basin identifier |
| `Ktrs_Air` | Water availability coefficient |

---

### 4. Land Cover Grid

Grid-based land cover dataset.

Required fields:

| Field | Description |
|---------|-------------|
| `ID` | Grid identifier |
| `PL` | Land cover class |
| `WADMPR` | Province code |
| `WADMKK` | Regency/Municipality code |
| `WADMKC` | District code |
| `WADMKD` | Village code |

---

### 5. Pollution Index Table

Pollution Index table describing water pollution conditions.

Required fields:

| Field | Description |
|---------|-------------|
| `Kab_Kota` | Regency/Municipality name |
| `Jumlah_Titik_Cemar_Ringan` | Number of lightly polluted monitoring points |
| `Jumlah_Titik_Cemar_Sedang` | Number of moderately polluted monitoring points |
| `Jumlah_Titik_Cemar_Berat` | Number of heavily polluted monitoring points |
| `Total` | Total monitoring points |

---

### 6. Population Distribution Grid

Population distribution model output.

Required field:

```text
POPGRIDYY
```

where:

- `YY` = last two digits of the analysis year

Example:

```text
POPGRID24
```

### Sample Data

Input data and sample datasets can be downloaded from:

[Download Here](https://1drv.ms/f/c/0192f2f41be57bd4/IgCLOA9DpbH4Qrg8M6ilrxYmAYxRISdnze0v97ejJmF3eCU?e=tTRSmN)

---

## Output

The algorithm produces an **IKP Air Grid Layer**.

Each grid contains:

| Field | Description |
|---------|-------------|
| `ID` | Grid identifier |
| `AIR_WS` | Available water resources |
| `AIR_CEMAR` | Polluted water volume |
| `AIR_LAYAK` | Usable water availability |
| `BA_POP` | Population water demand |
| `BA_PL` | Land-cover-based water demand |
| `BA_TOTAL` | Total water demand |
| `IKPAIR` | Water Utilization Capability Index |
| `KELAS_IKP` | IKP classification |
| `SKOR_IKP` | IKP score |

---

## Methodology

### Water Availability Assessment

Water provisioning services from the JLH Water Provision layer are aggregated within river basin areas.

Water availability is estimated using:

```text
AIR_WS
```

where:

- Water provisioning values (`PYA_YY_KK`)
- River basin water coefficients (`Ktrs_Air`)

are combined to estimate usable water resources.

---

### Water Quality Assessment

Pollution Index information is joined to the analysis grid.

The proportion of polluted water is estimated from:

- Light pollution
- Moderate pollution
- Heavy pollution

Output field:

```text
AIR_CEMAR
```

---

### Usable Water Availability

Usable water is calculated by subtracting polluted water from available water resources.

```text
AIR_LAYAK = AIR_WS - AIR_CEMAR
```

where:

- `AIR_WS` = available water
- `AIR_CEMAR` = polluted water

---

### Population Water Demand

Water demand from population is calculated using:

```text
BA_POP
```

derived from:

```text
POPGRIDYY
```

Population demand increases proportionally with population density.

---

### Land-Cover-Based Water Demand

Water demand is estimated from land cover classes.

Each land cover class is assigned a standard water demand coefficient.

Output field:

```text
BA_PL
```

---

### Total Water Demand

Total water demand is calculated as:

```text
BA_TOTAL = BA_POP + BA_PL
```

---

### IKP Air Calculation

The Water Utilization Capability Index is calculated as:

```text
IKPAIR = BA_TOTAL / AIR_LAYAK
```

where:

- `BA_TOTAL` = total water demand
- `AIR_LAYAK` = usable water availability

The resulting value represents pressure on available water resources.

---

### Classification

The resulting IKP values are classified into five categories.

| Score | Class |
|---------|---------|
| 5 | Very High |
| 4 | High |
| 3 | Moderate |
| 2 | Low |
| 1 | Very Low |

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
   - JLH Water Provision Grid
   - River Basin Layer (WS)
   - Land Cover Grid
   - Pollution Index Table
   - Population Distribution Grid
4. Identify the analysis year and construct year-dependent field names.
5. Calculate water availability (`AIR_WS`) using:
   - PYA ecosystem services
   - River basin coefficients.
6. Join Pollution Index information.
7. Calculate:
   - `AIR_CEMAR`
   - `AIR_LAYAK`
8. Calculate population water demand (`BA_POP`).
9. Calculate land-cover-based water demand (`BA_PL`).
10. Calculate:
    - `BA_TOTAL`
11. Calculate:
    - `IKPAIR`
12. Classify results into:
    - Very High
    - High
    - Moderate
    - Low
    - Very Low
13. Assign:
    - `KELAS_IKP`
    - `SKOR_IKP`
14. Generate the final IKP Air layer.

---

## Output Interpretation

### High IKP Values

Indicate:

- Adequate water availability
- Good water quality conditions
- Sustainable water utilization
- Lower pressure on water resources

### Moderate IKP Values

Indicate:

- Balanced water demand and availability
- Moderate environmental pressure
- Increased monitoring may be required

### Low IKP Values

Indicate:

- High water demand
- Limited water availability
- Significant pollution pressure
- Potential water resource deficits

### High SKOR_IKP

Indicates areas with strong water resource support capacity.

### Low SKOR_IKP

Indicates areas requiring water resource management and conservation measures.

---

## Applications

The resulting Water IKP dataset can be used for:

- Environmental Carrying Capacity (DDLH) analysis
- Water resource planning
- Watershed management
- Water security assessment
- Spatial planning
- Environmental policy development
- Climate adaptation planning
- D3TLH analysis workflows

---

## Notes

- All input datasets should use the same CRS.
- Population, land cover, and JLH data should represent the same analysis year.
- River basin boundaries should cover the entire analysis area.
- Pollution Index data must correspond to the analysis region.
- Water demand estimates depend on land cover classification quality.
- The quality of the final index depends on the accuracy of water provisioning, pollution, and population datasets.

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