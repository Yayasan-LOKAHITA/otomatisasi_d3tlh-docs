# Standarisasi Skema Data

## Overview

This module standardizes key thematic attributes used in D3TLH processing workflows by creating a consistent schema across datasets.

The algorithm allows users to map existing fields from an input layer to a predefined set of standardized fields. The names and data types of these fields are fixed according to the D3TLH standard.

All standardized fields are stored as **String** data types.

---

## Standardized Fields

The following fields are supported:

| Standard Field | Description |
|---------------|-------------|
| `LC` | Land Cover (Penutup Lahan) |
| `kwshutan` | Forest Area (Kawasan Hutan) |
| `KBA_250` | Landform Characteristic of the Ecoregion (Karakteristik Bentang Alam) |
| `KVA_250` | Natural Vegetation Characteristic of the Ecoregion (Karakteristik Vegetasi Alami) |

---

## Processing Workflow

1. Select the input layer.
2. Choose one or more source fields to map.
3. Assign source fields to the desired standardized fields.
4. Choose whether existing standardized fields should be overwritten.
5. Run the algorithm.
6. A new layer is created containing the standardized schema.

---

## Input Parameters

### Input Layer

Vector layer containing the source attributes.

Supported geometry types:

- Point
- Line
- Polygon

---

### Source Field for Land Cover → LC

Select the field containing land cover classifications.

The selected values will be copied into:

```text
LC
```

---

### Source Field for Forest Area → kwshutan

Select the field containing forest area classifications.

The selected values will be copied into:

```text
kwshutan
```

---

### Source Field for KBA → KBA_250

Select the field containing landform characteristic values.

The selected values will be copied into:

```text
KBA_250
```

---

### Source Field for KVA → KVA_250

Select the field containing natural vegetation characteristic values.

The selected values will be copied into:

```text
KVA_250
```

---

### Overwrite Existing Standardized Fields

When enabled, existing standardized fields will be updated with values from the selected source fields.

**Default:** Enabled

| Option | Description |
|----------|-------------|
| Enabled | Existing values in standardized fields are replaced |
| Disabled | Processing stops if a standardized field already exists |

---

## Output Schema

The output layer contains all original attributes plus the selected standardized fields.

### LC

| Attribute | Description |
|------------|-------------|
| LC | Land Cover classification |

### kwshutan

| Attribute | Description |
|------------|-------------|
| kwshutan | Forest Area classification |

### KBA_250

| Attribute | Description |
|------------|-------------|
| KBA_250 | Landform Characteristic of the Ecoregion |

### KVA_250

| Attribute | Description |
|------------|-------------|
| KVA_250 | Natural Vegetation Characteristic of the Ecoregion |

All standardized fields are stored as **String** values.

---

## Notes

- At least one source field must be selected.
- Original attributes are preserved.
- The input layer is not modified.
- Output is written to a new layer.
- Standardized field names cannot be changed.
- All output values are converted to text format.

---

## Common Issues

### No Source Fields Selected

**Message**

```text
Select at least one source field (LC/kwshutan/KBA_250/KVA_250).
```

**Solution**

Choose at least one source field before running the algorithm.

---

### Standardized Field Already Exists

**Message**

```text
Field '<field_name>' already exists.
```

**Solution**

Either:

- Enable **Overwrite Existing Standardized Fields**, or
- Remove/rename the existing field before processing.

---

## Example Mapping

| Source Field | Standardized Field |
|-------------|-------------------|
| PL_2024 | LC |
| FUNGSI_KWS | kwshutan |
| EKOREGION_KBA | KBA_250 |
| EKOREGION_KVA | KVA_250 |

Result:

```text
Input Layer
├── PL_2024
├── FUNGSI_KWS
├── EKOREGION_KBA
└── EKOREGION_KVA

Output Layer
├── PL_2024
├── FUNGSI_KWS
├── EKOREGION_KBA
├── EKOREGION_KVA
├── LC
├── kwshutan
├── KBA_250
└── KVA_250
```

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