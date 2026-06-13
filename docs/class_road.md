# Standardisasi Kelas Jalan (KJLN)

## Overview

This module standardizes road classes for use in population distribution modeling.

The algorithm maps road class values from an input road layer to a predefined set of **KJLN (Kelas Jalan)** categories. The standardized class is stored in the `KJLN` field of the output layer while preserving the original input data.

---

## How to Use

1. Select the road layer.
2. Select the source field containing the original road class values.
3. Click **Run**.
4. A mapping dialog will appear:
   - **Left panel**: Unique values from the source road-class field.
   - **Right panel**: Dropdown list containing the standard KJLN classes.
5. Assign each source value to the appropriate KJLN category.
6. Optionally:
   - Use **Load JSON** to load a previously saved mapping.
   - Use **Save JSON** to save the current mapping for future use.
7. Enable **Only fill when KJLN is NULL** if you want to preserve existing KJLN values.
8. Execute the process.

---

## Standard KJLN Classes

| KJLN Class | English Description |
|------------|---------------------|
| Jalan Arteri | Arterial Road |
| Jalan Kolektor | Collector Road |
| Jalan Lokal | Local Road |
| Jalan Lain | Other Road |
| Jalan Layang | Elevated Road |
| Jalan Sedang Dibangun | Road Under Construction |
| Jalan Setapak | Footpath / Trail |
| Jalan Tol Dua Jalur Dengan Pemisah Fisik | Dual Carriageway Toll Road with Physical Median |
| Jalan Tol Dua Jalur Tanpa Pemisah Fisik | Dual Carriageway Toll Road without Physical Median |
| Jalan Tol Layang | Elevated Toll Road |
| Jalan/Transportasi Darat Lainnya | Other Land Transportation Infrastructure |
| Pematang | Dike / Embankment |

---

## Additional Options

### Load JSON

Loads a previously saved mapping configuration and automatically assigns source road classes to KJLN categories.

### Save JSON

Saves the current mapping configuration to a JSON file for reuse in future projects.

### Only Fill When KJLN is NULL

When enabled, the algorithm updates only features where the `KJLN` field is empty (`NULL`).

This option is useful when:

- Updating partially classified datasets.
- Preventing overwriting of existing classifications.
- Incrementally improving road-class mappings.

---

## Output

The output layer contains all original attributes plus a standardized `KJLN` field.

| Field | Description |
|---------|-------------|
| KJLN | Standardized road class used for population distribution modeling |

The original input layer remains unchanged.