# JLH & IKP Standard Symbology

## Overview

This module applies standardized cartographic symbology to **JLH (Jasa Lingkungan Hidup)** and **IKP (Indeks Kemampuan Pemanfaatan)** datasets directly within the selected layer.

The algorithm automatically identifies the appropriate classification field and applies a categorized renderer using the standard D3TLH visualization scheme. No new layer is created; the symbology is applied directly to the existing layer.

The resulting map follows the standard D3TLH classification and color convention, ensuring consistency across environmental assessments and reporting products.

---

## Purpose

To standardize the visualization of JLH and IKP datasets by applying predefined categories and color schemes.

The module provides:

* Consistent D3TLH map visualization
* Automatic category field detection
* Support for JLH and IKP outputs
* In-place symbology application
* Standardized environmental mapping outputs

---

## Supported Themes

### 1. JLH (Jasa Lingkungan Hidup)

Supports standardized symbology for ecosystem service outputs generated from D3TLH workflows.

Examples include:

* Penyedia Air
* Penyedia Pangan
* Pengatur Tata Air
* Pengatur Iklim
* Habitat Biodiversitas
* Other JLH outputs

### 2. IKP (Indeks Kemampuan Pemanfaatan)

Supports standardized symbology for:

* IKP Air
* IKP Lahan
* IKP Kehati
* IKP Udara
* Other IKP-based outputs

---

## Classification Categories

### Standard Categories

The following categories are supported:

| Indonesian    | English   |
| ------------- | --------- |
| Sangat Rendah | Very Low  |
| Rendah        | Low       |
| Sedang        | Medium    |
| Tinggi        | High      |
| Sangat Tinggi | Very High |

### Additional Category for IKP Lahan

| Indonesian     | English      |
| -------------- | ------------ |
| Tidak Dihitung | Not Computed |

This category is used for areas excluded from the Land IKP calculation.

---

## Required Inputs

### 1. Target Layer

A vector layer containing JLH or IKP classification fields.

### 2. Theme

Select the appropriate visualization theme:

* JLH
* IKP

### 3. Year (Optional)

Used for JLH outputs.

The year is converted into a two-digit suffix to identify the classification field.

Examples:

| Year | Field Suffix |
| ---- | ------------ |
| 2024 | `_24`        |
| 2025 | `_25`        |
| 2026 | `_26`        |

Example field names:

```text
KELAS_PYA_24
KELAS_PPK_25
KELAS_PGA_26
```

### 4. Category Field (Optional)

Specify a category field manually to override automatic field detection.

If left empty, the module attempts to detect the appropriate classification field automatically.

---

## Output

The module does not create a new layer.

Instead, it updates the symbology of the selected layer by applying:

* Categorized Renderer
* Standard D3TLH color scheme
* Standard category labels

The output is:

| Item              | Description                  |
| ----------------- | ---------------------------- |
| Symbology         | Updated categorized renderer |
| Layer             | Same input layer             |
| New Layer         | No                           |
| Attribute Changes | No                           |

---

## Methodology

### Automatic Field Detection

The module searches for classification fields based on:

* Selected Theme
* Selected Year
* D3TLH naming conventions

Examples:

```text
KELAS_PYA_24
KELAS_PGA_24
KELAS_PPK_24
KELAS_IKP
```

---

### Category Identification

The detected field is evaluated and categorized according to the standard D3TLH classes.

Recognized values include:

```text
Sangat Rendah
Rendah
Sedang
Tinggi
Sangat Tinggi
```

and for Land IKP:

```text
Tidak Dihitung
```

---

### Symbology Application

A categorized renderer is created and applied directly to the selected layer.

The renderer uses the official D3TLH category colors and labels.

No attribute values are modified during the process.

---

## Processing Workflow

1. Select the target layer.
2. Select the visualization theme:

   * JLH
   * IKP
3. Optionally specify the analysis year.
4. Optionally specify a category field name.
5. The module detects the appropriate classification field.
6. Categories are extracted from the field.
7. Standard D3TLH symbology is generated.
8. The categorized renderer is applied directly to the selected layer.
9. The layer is refreshed in the QGIS interface.

---

## Output Interpretation

### Very High / Sangat Tinggi

Represents the highest environmental capacity or ecosystem service value.

### High / Tinggi

Represents above-average environmental capacity or ecosystem service value.

### Medium / Sedang

Represents moderate environmental capacity or ecosystem service value.

### Low / Rendah

Represents below-average environmental capacity or ecosystem service value.

### Very Low / Sangat Rendah

Represents the lowest environmental capacity or ecosystem service value.

### Not Computed / Tidak Dihitung

Represents areas excluded from the analysis or areas where calculations were not performed.

---

## Applications

The module can be used for:

* D3TLH map production
* JLH visualization
* IKP visualization
* Environmental reporting
* Spatial planning products
* Environmental carrying capacity assessment
* Standardized map preparation
* D3TLH workflow automation

---

## Notes

* The selected layer must contain a valid classification field.
* The year parameter is only used for JLH themes.
* If the category field is specified manually, automatic detection is skipped.
* Existing symbology will be replaced.
* No attribute data are modified.
* No new layer is created.
* The module only updates layer visualization properties.

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