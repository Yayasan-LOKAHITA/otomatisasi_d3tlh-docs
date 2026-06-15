# Population Distribution Model

## Overview

This module models population distribution using scores and weights derived from land cover and road network parameters, producing a gridded population distribution dataset.

The methodology allocates population counts from administrative units into grid cells based on the relative influence of land cover characteristics and road accessibility. The resulting grid-based population model can be used for environmental carrying capacity assessments, ecosystem service analysis, and spatial planning.

---

## Purpose

To distribute population data from administrative units into spatial grid cells using weighted parameters derived from:

* Land Cover (`PL`)
* Road Network (`KJLN`)
* Administrative Boundaries
* Population Statistics

This approach generates a more spatially explicit representation of population distribution than conventional administrative-level datasets.

---

## Required Inputs

### 1. Administrative Boundaries Layer

The administrative boundary layer must contain standardized administrative codes and population data.

Required fields:

* `WADMPR` — Province Code
* `WADMKK` — Regency/Municipality Code
* `WADMKC` — District Code
* `WADMKD` — Village Code
* `POPMYY` — Population field (e.g., `POPM24` for year 2024)

### 2. Grid Layer

Grid layer generated using the Utility module.

Required field:

* `ID`

### 3. Land Cover Layer

Vector land cover dataset containing:

* `PL`

### 4. Road Network Layer

Vector road network dataset containing:

* `KJLN`

---

## Output

The algorithm produces a **Population Distribution Model** in grid format.

Each grid cell contains:

| Field       | Description                       |
| ----------- | --------------------------------- |
| `ID`        | Grid identifier                   |
| `WADM**`    | Administrative code               |
| `POPMYY`    | Population of administrative unit |
| `WPLYY`     | Land cover weight                 |
| `WJLNYY`    | Road network weight               |
| `WGRIDYY`   | Combined grid weight              |
| `WADMYY`    | Total administrative weight       |
| `POPGRIDYY` | Distributed population value      |

---

## Methodology

The model uses a weighted allocation approach based on land cover and road network characteristics.

### Land Cover Weight (WPLYY)

The grid is intersected with the land cover layer.

Land cover classes are assigned predefined scores and weights, producing:

```text
WPLYY
```

### Road Network Weight (WJLNYY)

The grid is intersected with the road network layer.

Road classes are assigned predefined scores and weights, producing:

```text
WJLNYY
```

### Combined Grid Weight

The total grid weight is calculated as:

```text
WGRIDYY = WPLYY + WJLNYY
```

### Administrative Weight

For each administrative unit:

```text
WADMYY = Σ(WGRIDYY)
```

### Population Allocation

Population is distributed proportionally according to each grid cell's weight:

```text
POPGRIDYY = floor((WGRIDYY / WADMYY) × POPMYY)
```

---

## Processing Workflow

1. Harmonize the coordinate reference system (CRS) of all input datasets.
2. Repair invalid geometries and create spatial indexes.
3. Standardize administrative boundary fields to:

   * `WADMPR`
   * `WADMKK`
   * `WADMKC`
   * `WADMKD`
   * `POPMYY`
4. Transfer administrative attributes (`WADM**`) into the Grid layer using the Maximum Combined Area (MCA) approach.
5. Join population values (`POPMYY`) from administrative boundaries into the Grid layer.
6. Intersect the Grid layer with the Land Cover layer and calculate:

   * `WPLYY`
7. Intersect the Grid layer with the Road Network layer and calculate:

   * `WJLNYY`
8. Calculate:

   * `WGRIDYY`
   * `WADMYY`
   * `POPGRIDYY`
9. Standardize output field names.
10. Generate the final Population Distribution Model.

---

## Output Interpretation

### High POPGRIDYY Values

Indicate grid cells with:

* Higher accessibility
* More intensive land use
* Greater likelihood of population concentration

### Low POPGRIDYY Values

Indicate grid cells with:

* Limited accessibility
* Sparse land use
* Lower population density

---

## Applications

The resulting population distribution model can be used for:

* Environmental Carrying Capacity (DDLH) analysis
* Ecosystem Service assessment
* Spatial planning
* Infrastructure planning
* Disaster risk assessment
* Population exposure analysis
* Environmental quality assessment
* D3TLH analysis workflows

---

## Notes

* All input layers should use the same CRS.
* Administrative fields must follow the standardized naming convention.
* Population fields should follow the `POPMYY` format.
* The quality of the model depends heavily on the quality of land cover, road network, and population datasets.
* Grid resolution influences the spatial detail of the final population distribution model.

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