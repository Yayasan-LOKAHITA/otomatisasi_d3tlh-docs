# Indonesian Multi-scale Grid System (IMGS)

The **Indonesian Multi-scale Grid System (IMGS)** is designed as a square-cell grid structure similar to a raster data format. Each cell has a unique coordinate and attributes that enable the continuous and structured representation of geographic phenomena.

IMGS adopts the **Indonesian Geospatial Reference System (SRGI) 2013** as the national geodetic reference, with its origin located at **90° E longitude** and **15° S latitude** to align with the numbering system of the Indonesian Topographic Base Map (**RBI**) sheets.

## Available Grid Sizes

| Grid Size | Approximate Cell Size |
|------------|----------------------|
| 1° × 1°30' | ~111.0 × 166.5 km |
| 30' × 30' | ~55.50 × 55.50 km |
| 15' × 15' | ~27.75 × 27.75 km |
| 7'30" × 7'30" | ~13.875 × 13.875 km |
| 2'30" × 2'30" | ~4.625 × 4.625 km |
| 30" × 30" | ~0.900 × 0.900 km |
| 5" × 5" | ~0.150 × 0.150 km |

## Administrative Attributes

In addition to the grid geometry, administrative boundary attributes are added from the **village/sub-district level** up to the **province level** based on the provided Administrative Boundary layer.

## Output Fields

The generated IMGS layer contains the following attributes:

- `ID`
- `WADMKD`
- `WADMKC`
- `WADMKK`
- `WADMPR`

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