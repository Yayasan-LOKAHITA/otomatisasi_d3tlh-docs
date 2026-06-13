# Dominant Attribute by Maximum Combined Area (MCA)

This algorithm calculates the dominant attribute from **Layer 2** for each polygon in **GRID** based on the largest combined area of intersection (**MCA – Maximum Combined Area**).

## Processing Workflow

1. Intersect **GRID** with **Layer 2** to obtain the area for each combination.
2. Dissolve by **GRID ID** and **Layer 2 class** to sum intersected areas.
3. Calculate area in square meters (**m²**) using a transformation to **EPSG:3857**.
4. Determine the maximum area for each **GRID ID**.
5. Join the maximum area values back to the dissolved layer.
6. Extract features where the area equals the maximum area (dominant class).
7. Join the dominant class back to the original **GRID** layer.

## Inputs

**1. GRID**

Polygon layer containing a unique identifier field (`id` or `ID`).

**2. Layer 2**

Polygon layer containing the classification field whose dominant value will be assigned to each GRID polygon.

## Output

A **GRID** layer with an additional field containing the dominant class from **Layer 2** based on the Maximum Combined Area (MCA) method.

---

## Author

**Yayasan Lokahita**

- Fadillah Azhar Deaudin Kurniawan
- Sitarani Safitri
- Dini Aprilia Norvyani
- Suchi Rahmadani
- Fariz Rizaldy Wibowo

### Supported By

**Kementerian Lingkungan Hidup Republik Indonesia**