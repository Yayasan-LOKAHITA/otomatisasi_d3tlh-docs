# Ecological Footprint Calculation

## Overview

This module calculates the **Ecological Footprint (Jejak Ekologis)** of a region based on statistical data representing population consumption and land requirements.

The ecological footprint measures the amount of biologically productive land and water area required to support human activities, including food consumption, clothing needs, housing requirements, and built-up areas.

The resulting table can be used as an input for environmental carrying capacity analysis, sustainable development assessments, and D3TLH workflows.

---

## Purpose

To calculate the ecological footprint of a region and estimate the total land area required to support the population's resource consumption.

The analysis produces:

* Ecological Footprint per Capita per Year
* Total Land Requirement (Hectares)
* Ecological Footprint Components by Sector

---

## Required Inputs

### 1. Statistical Data Table

Prepare the statistical data using the standardized Excel template.

**Template File:**

[Download Here](https://1drv.ms/f/c/0192f2f41be57bd4/IgBoqXHS_LkJSrHmeENI4PodAcUQA_-LVZRzkBGzsJ5_W5I?e=xBRcYy)

The template contains all required statistical variables for ecological footprint calculations.

---

## Output

The module generates an **Ecological Footprint Table** containing the following fields:

| Field         | Description                                    |
| ------------- | ---------------------------------------------- |
| `TAHUN`       | Analysis year                                  |
| `POPULASI`    | Total population                               |
| `PANGAN`      | Ecological footprint from food consumption     |
| `SANDANG`     | Ecological footprint from clothing consumption |
| `PAPAN`       | Ecological footprint from housing requirements |
| `BUILTUP`     | Ecological footprint from built-up land use    |
| `EF_CAP_YEAR` | Ecological footprint per capita per year       |
| `TOTAL_HA`    | Total land requirement (hectares)              |

---

## Methodology

The ecological footprint is calculated by estimating land requirements for various consumption categories and aggregating them into a single footprint indicator.

### Food Component (PANGAN)

Represents the biologically productive land required to support food consumption.

Output field:

```text
PANGAN
```

### Clothing Component (SANDANG)

Represents land requirements associated with clothing and textile consumption.

Output field:

```text
SANDANG
```

### Housing Component (PAPAN)

Represents land requirements associated with residential needs and housing infrastructure.

Output field:

```text
PAPAN
```

### Built-up Component (BUILTUP)

Represents land occupied by settlements, infrastructure, and other developed areas.

Output field:

```text
BUILTUP
```

### Ecological Footprint per Capita

The total ecological footprint per person is calculated as:

```text
EF_CAP_YEAR = PANGAN + SANDANG + PAPAN + BUILTUP
```

### Total Land Requirement

The total ecological footprint for the population is calculated as:

```text
TOTAL_HA = EF_CAP_YEAR × POPULASI
```

where:

* `EF_CAP_YEAR` = Ecological Footprint per Capita per Year
* `POPULASI` = Total Population

---

## Processing Workflow

1. Download and prepare the statistical data template.
2. Populate all required statistical variables in the Excel template.
3. Validate the completeness and consistency of the input data.
4. Load the completed Excel file into the module.
5. Calculate ecological footprint components:

   * `PANGAN`
   * `SANDANG`
   * `PAPAN`
   * `BUILTUP`
6. Calculate:

   * `EF_CAP_YEAR`
   * `TOTAL_HA`
7. Generate the final Ecological Footprint Table.
8. Save the output table to the selected workspace or temporary directory.

---

## Output Interpretation

### High EF_CAP_YEAR Values

Indicate:

* Higher resource consumption per capita
* Greater environmental demand
* Larger ecological footprint per person

### Low EF_CAP_YEAR Values

Indicate:

* Lower resource consumption per capita
* Reduced environmental pressure
* Smaller ecological footprint per person

### High TOTAL_HA Values

Indicate:

* Large land requirements to support the population
* Higher pressure on environmental resources
* Potential ecological deficit if available land is insufficient

### Low TOTAL_HA Values

Indicate:

* Lower overall land requirements
* Reduced environmental pressure
* Greater potential for sustainable resource use

---

## Applications

The resulting ecological footprint dataset can be used for:

* Environmental Carrying Capacity (DDLH) analysis
* Environmental Support Capacity assessment
* Ecological Deficit and Ecological Reserve analysis
* Sustainable development evaluation
* Spatial planning support
* Environmental policy assessment
* Natural resource management
* D3TLH analysis workflows

---

## Notes

* Input data must follow the provided Excel template format.
* Statistical data should be consistent and originate from verified sources.
* All calculations are performed on an annual basis.
* Ecological footprint values are expressed in hectares.
* The quality of the results depends on the completeness and accuracy of the input statistical data.

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