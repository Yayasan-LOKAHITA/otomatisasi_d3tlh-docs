# Penambahan Atribut Pulau

## Overview

This module automatically assigns an island name (`PULAU`) to each feature based on its geographic location.

The algorithm uses predefined island boundary polygons covering the major island groups of Indonesia and classifies each feature according to the location of its centroid.

If a centroid falls outside all predefined island polygons, the algorithm assigns the nearest island using a distance-based fallback method.

---

## Purpose

This tool standardizes island attribution for spatial datasets used in D3TLH processing workflows.

The generated `PULAU` attribute can be used for:

- Regional analysis
- Data aggregation by island
- Reporting and statistics
- Quality control and validation
- Subsequent D3TLH processing modules

---

## Processing Workflow

1. Select the input layer.
2. Choose whether existing `PULAU` values should be overwritten.
3. Run the algorithm.
4. The layer is automatically reprojected to EPSG:4326.
5. The centroid of each feature is calculated.
6. The centroid is checked against predefined island polygons.
7. If no polygon match is found, the nearest island is determined using geographic distance.
8. A new layer with the `PULAU` attribute is generated.

---

## Input Parameters

### Input Layer

Vector layer to be classified.

Supported geometry types:

- Point
- Line
- Polygon

---

### Overwrite Existing PULAU Values

Determines whether existing values in the `PULAU` field should be replaced.

| Option | Description |
|----------|-------------|
| Enabled | Existing `PULAU` values are replaced |
| Disabled | Existing values are preserved |

**Default:** Disabled

---

## Classification Method

### Step 1 – Coordinate Standardization

The input layer is automatically reprojected to:

```text
EPSG:4326 (WGS 84)
```

to ensure consistent geographic calculations.

---

### Step 2 – Centroid Calculation

For each feature, the algorithm calculates the centroid location.

The centroid is used as the representative position for island classification.

---

### Step 3 – Island Polygon Classification

The centroid is tested against predefined island polygons representing:

- Sumatera
- Jawa
- Bali–Nusa Tenggara
- Kalimantan
- Sulawesi
- Maluku
- Papua

If the centroid falls inside one of these polygons, the corresponding island name is assigned.

---

### Step 4 – Nearest Island Fallback

If a centroid does not intersect any island polygon, the algorithm determines the nearest island using the Haversine distance formula.

This ensures that all features receive a valid island classification.

---

## Island Categories

The algorithm assigns one of the following values:

| PULAU Value |
|-------------|
| Sumatera |
| Jawa |
| Bali–Nusra |
| Kalimantan |
| Sulawesi |
| Maluku |
| Papua |

---

## Output

The output layer contains all original attributes plus the `PULAU` field.

| Field | Description |
|---------|-------------|
| PULAU | Assigned island classification |

---

## Output Example

| Feature | Assigned PULAU |
|----------|---------------|
| Lampung | Sumatera |
| Bandung | Jawa |
| Denpasar | Bali–Nusra |
| Samarinda | Kalimantan |
| Makassar | Sulawesi |
| Ambon | Maluku |
| Jayapura | Papua |

---

## Notes

- The original input layer is not modified.
- The output is written to a new layer.
- Classification is based on feature centroids.
- The algorithm does not require external island boundary datasets.
- Island boundaries are embedded directly within the plugin.

---

## Common Issues

### Unexpected Island Assignment

Because classification uses feature centroids, very large geometries spanning multiple islands may be assigned based on the centroid location rather than total area coverage.

---

### Features Near Island Boundaries

Features located close to island boundaries may be assigned using the nearest-island fallback method if the centroid falls outside predefined polygon extents.

---

## Technical Details

### Coordinate Reference System

All processing is performed using:

```text
EPSG:4326 (WGS 84)
```

### Distance Calculation

Nearest-island classification uses the Haversine formula to calculate great-circle distances between geographic coordinates.

### Embedded Island Boundaries

The algorithm contains predefined polygon boundaries for Indonesia's major island groups and does not require external reference layers.

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