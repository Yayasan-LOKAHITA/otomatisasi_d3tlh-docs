# Air Utilization Capability Index (IKP Udara)

## Overview

This module calculates the **Air Utilization Capability Index (IKP Udara)**, an indicator used to assess the capability of an area to absorb, assimilate, and neutralize air pollution loads while maintaining healthy air quality for humans and ecosystems.

The methodology integrates air pollution concentration data and climate change indicators to evaluate the environmental capacity of an area in supporting sustainable air quality conditions.

The resulting index can be used for environmental carrying capacity assessments, air quality management, climate adaptation planning, and D3TLH workflows.

---

## Purpose

To evaluate the capability of an area to maintain acceptable air quality conditions by considering:

* Air pollution concentration
* Climate change impacts
* Atmospheric environmental capacity
* Ecosystem resilience to air pollution

The analysis produces:

* Air Utilization Capability Index (IKP Udara)
* Air Quality Capability Classification
* Air Quality Capability Score
* Grid-based air quality assessment
* Polygon-based air quality assessment

---

## Required Inputs

### 1. KPKU Grid Layer

Vector grid dataset representing spatial analysis units.

Required field:

* `ID`

### 2. PM2.5 Raster (Time-Averaged)

Raster dataset representing average PM2.5 concentration.

The raster is used to evaluate air pollution pressure within each grid.

### 3. Temperature Projection Layer

Vector dataset representing projected temperature conditions and climate change impacts.

Required field:

* `SKOR`

The `SKOR` field represents the temperature projection score used in the IKP calculation.

### Sample Data

Temperature projection data can be downloaded from:

[Download Here](https://1drv.ms/f/c/0192f2f41be57bd4/IgCxwuHXDTHRQrR_-uUh04PLAQsWf6WY_xJBDuEN28FsY80?e=inIRNT)

---

## Output

The algorithm produces:

### 1. Air IKP Polygon Layer

Spatial air quality capability assessment aggregated into polygon units.

### 2. Air IKP Grid Layer

Grid-based air quality capability assessment.

Each grid contains:

| Field       | Description                      |
| ----------- | -------------------------------- |
| `ID`        | Grid identifier                  |
| `PM25`      | Average PM2.5 concentration      |
| `SKOR_SUHU` | Temperature projection score     |
| `IKP_UDARA` | Air Utilization Capability Index |
| `KELAS_IKP` | IKP classification               |
| `SKOR_IKP`  | IKP score                        |

---

## Methodology

The Air IKP is derived by integrating air pollution conditions and climate-related environmental pressure.

### PM2.5 Assessment

The PM2.5 raster is summarized within each analysis grid.

The resulting value represents average pollution concentration.

Output field:

```text
PM25
```

Higher PM2.5 values indicate greater air pollution pressure.

---

### Temperature Projection Assessment

The Temperature Projection layer is intersected with the analysis grid.

The algorithm extracts the temperature projection score from:

```text
SKOR
```

which represents projected climate stress on air quality and ecosystem health.

Output field:

```text
SKOR_SUHU
```

---

### Air Capability Calculation

Air capability is evaluated by combining:

* Air pollution pressure (PM2.5)
* Temperature projection score
* Environmental assimilation capacity

Conceptually:

```text
IKP_UDARA = f(PM25, SKOR_SUHU)
```

where:

* `PM25` = Air pollution concentration
* `SKOR_SUHU` = Temperature projection score

The resulting index represents the capability of an area to maintain healthy air quality under current and future environmental conditions.

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

1. Harmonize the coordinate reference system (CRS) of all input datasets.
2. Repair invalid geometries and create spatial indexes.
3. Load:

   * KPKU Grid
   * PM2.5 Raster
   * Temperature Projection Layer
4. Ensure the Temperature Projection layer contains the `SKOR` field.
5. Calculate average PM2.5 concentration within each grid.
6. Transfer temperature projection scores into the grid layer.
7. Standardize indicator values.
8. Calculate:

   * `IKP_UDARA`
9. Classify IKP values into:

   * Very High
   * High
   * Moderate
   * Low
   * Very Low
10. Assign:

    * `KELAS_IKP`
    * `SKOR_IKP`
11. Generate polygon outputs.
12. Generate grid outputs.

---

## Output Interpretation

### High IKP Values

Indicate:

* Better air quality conditions
* Lower pollution pressure
* Higher atmospheric assimilation capacity
* Greater environmental resilience
* Better support for ecosystem and human health

### Moderate IKP Values

Indicate:

* Manageable air quality conditions
* Moderate environmental pressure
* Potential vulnerability to future pollution increases

### Low IKP Values

Indicate:

* High PM2.5 concentrations
* Significant environmental pressure
* Reduced air quality support capacity
* Increased health and ecosystem risks

### High SKOR_IKP

Indicates areas with strong capability to maintain healthy air quality.

### Low SKOR_IKP

Indicates areas requiring air quality improvement measures and environmental management interventions.

---

## Applications

The resulting Air IKP dataset can be used for:

* Environmental Carrying Capacity (DDLH) analysis
* Air quality assessment
* Climate change adaptation planning
* Environmental health studies
* Pollution management
* Spatial planning
* Ecosystem vulnerability assessment
* Biodiversity IKP integration
* D3TLH analysis workflows

---

## Notes

* All input datasets should use the same CRS.
* PM2.5 raster resolution influences the spatial detail of the analysis.
* The Temperature Projection layer must contain a valid `SKOR` field.
* Climate change indicators significantly influence the resulting index.
* It is recommended not to save outputs as temporary layers.
* The quality of the results depends on the accuracy and temporal consistency of the PM2.5 and temperature projection datasets.

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