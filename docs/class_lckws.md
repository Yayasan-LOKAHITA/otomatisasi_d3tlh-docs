# Klasifikasi Penutupan Lahan & Kawasan Hutan (KLHK RI)

## Overview

This algorithm classifies features into **Land Cover (PL)** or **Forest Area (Kawasan Hutan)** classes using internal lookup tables bundled with the plugin.

No external CSV input is required from the user. The algorithm automatically loads the appropriate classification database and assigns classification labels based on the selected identifier field.

---

## Processing Workflow

1. Select the input layer.
2. Choose the classification type.
3. Select the field containing the classification code.
4. Load the corresponding internal lookup table.
5. Match input values against the lookup table.
6. Create a new classification field.
7. Generate the output layer.

---

## Input Parameters

### Input Layer

Vector layer containing the classification identifier.

Supported geometry types:

- Point
- Line
- Polygon

### Classification Type

Choose the classification scheme to apply.

| Option | Description |
|----------|-------------|
| Penutup Lahan (PL) | Land Cover classification |
| Kawasan Hutan (kwshutan) | Forest Area classification |

### ID Field

Field containing the classification code to be matched against the lookup table.

Examples:

- `PL2024_ID`
- `fungsikws`
- `CODE`

### Treat ID as Text

Preserves the original formatting of identifier values, including leading zeros.

**Default:** Enabled

### Match Numeric IDs with or without Leading Zeros

Allows matching of equivalent numeric values regardless of formatting.

Examples:

| Input Value | Lookup Value |
|-------------|-------------|
| `1` | `001` |
| `001` | `1` |
| `0005` | `5` |

**Default:** Enabled

---

## Output

The output layer contains all original attributes plus an additional classification field.

### Penutup Lahan Output

| Field | Description |
|---------|-------------|
| PL | Land cover classification |

### Kawasan Hutan Output

| Field | Description |
|---------|-------------|
| kwshutan | Forest area classification |

---

## Common Issues

### ID Field Not Found

**Message**

```text
ID field not found in input layer.
```

**Solution**

Verify that the selected identifier field exists in the input dataset.

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