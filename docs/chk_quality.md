# Perbaikan Kualitas Data

## Overview

This module performs basic data quality validation by repairing invalid geometries in the input layers before they are used in subsequent D3TLH processing workflows.

The algorithm applies the QGIS **Fix Geometries** tool to the **Land Cover (Penutup Lahan)** and **Ecoregion (Ekoregion)** layers and produces cleaned outputs that are ready for spatial analysis.

---

## Purpose

Spatial datasets often contain geometry errors such as:

- Self-intersections
- Duplicate vertices
- Invalid polygon rings
- Geometry inconsistencies

These issues may cause failures or inaccurate results in overlay, intersection, dissolve, and other spatial operations.

This algorithm automatically repairs such issues using the QGIS geometry validation engine.

---

## Processing Workflow

1. Select the **Land Cover (Penutup Lahan)** layer.
2. Select the **Ecoregion (Ekoregion)** layer.
3. Optionally provide a **KEE** layer.
4. Run the algorithm.
5. The algorithm executes the **Fix Geometries** process on:
   - Land Cover layer
   - Ecoregion layer
6. New layers with corrected geometries are generated.

---

## Input Parameters

### Penutup Lahan

Land Cover layer that will undergo geometry validation and repair.

Supported geometry types:

- Point
- Line
- Polygon

---

### Ekoregion

Ecoregion layer that will undergo geometry validation and repair.

Supported geometry types:

- Point
- Line
- Polygon

---

### KEE (Optional)

Key Ecological Ecosystem (KEE) layer.

This parameter is currently optional and is not modified by the algorithm.

---

## Processing Method

The algorithm internally runs the QGIS processing tool:

```text
qgis:fixgeometries
```

on both required input layers.

The resulting layers contain repaired geometries while preserving:

- Original attributes
- Coordinate Reference System (CRS)
- Geometry type

---

## Output Layers

### Penutup Lahan Fixed

A copy of the Land Cover layer with repaired geometries.

| Property | Description |
|-----------|-------------|
| Geometry | Corrected |
| Attributes | Preserved |
| CRS | Preserved |

---

### Ekoregion Fixed

A copy of the Ecoregion layer with repaired geometries.

| Property | Description |
|-----------|-------------|
| Geometry | Corrected |
| Attributes | Preserved |
| CRS | Preserved |

---

## Benefits

Running this validation step before further processing helps to:

- Prevent topology-related processing failures
- Improve overlay and intersection accuracy
- Ensure compatibility with subsequent D3TLH workflows
- Reduce errors during spatial analysis

---

## Notes

- The original input layers are not modified.
- Output layers are written as new datasets.
- Attribute tables remain unchanged.
- Geometry repair follows the implementation of the QGIS **Fix Geometries** tool.
- It is recommended to run this tool before performing overlay or intersection operations.

---

## Common Issues

### Invalid Geometry Errors in Subsequent Processing

If spatial operations fail due to geometry errors, rerun this tool and use the corrected output layers.

---

### Empty Output Layer

Possible causes:

- Invalid input source
- Corrupted geometry dataset
- Unsupported geometry structure

Verify the integrity of the source dataset before processing.

---

## Example Workflow

```text
Raw Land Cover Layer
        │
        ▼
 Fix Geometries
        │
        ▼
Land Cover Fixed
```

```text
Raw Ecoregion Layer
        │
        ▼
 Fix Geometries
        │
        ▼
Ecoregion Fixed
```

The resulting layers can then be used safely in clipping, intersection, dissolve, and other D3TLH processing modules.

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