# AC-PIDNN
Daily Global Sea Surface Ageostrophic Current Dataset from 1993–2023 via Physics-Informed Deep Learning

**DataSet**
DOI/URL:https://zenodo.org/records/19966716

**Authors/Creators:**

* **Cui, Guangxi** (Data collector, University of Macau)
* **Cai, Zhongya** (Contact person, University of Macau)

---

## 1. Dataset Overview

This dataset provides a daily, high-resolution (0.25°) reconstruction of global sea surface circulation spanning a 31-year period from January 1, 1993, to December 31, 2023. The reconstruction accurately models ocean dynamics by explicitly accounting for key physical drivers, including wind stress, non-linear effects, and the Coriolis force. It separates the total flow field into geostrophic, Ekman, and non-linear advective components, providing a comprehensive view of global surface currents.

---

## 2. Data Format and CF Standard Compliance

* **Format:** NetCDF-4 Classic (`netcdf4_classic`)
* **Standard Compliance:** The NetCDF files have been formatted to comply with the Climate and Forecast Metadata Conventions (**CF-1.8**).
* **Software Compatibility:** All spatial and temporal dimensions, variable names, units, and missing values conform to standard conventions to ensure seamless integration with standard Earth science software (e.g., Python `xarray`, MATLAB, CDO, Panoply).

---

## 3. Directory Structure and Naming Conventions

The dataset contains daily files spanning 31 years. The data is systematically organized into subdirectories by year and month. Each daily file follows a standard path structure:

```text
Structure: [YYYY]/[MM]/[YYYY]_[MM]_[DD].nc

Examples:
1993/01/1993_01_01.nc
1993/01/1993_01_02.nc

```

---

## 4. Variables, Units, and Missing Values

The data variables are defined on a 1440 (longitude) × 720 (latitude) grid. Missing data points (e.g., over landmasses or un-computable grid points) are designated with a standard missing value indicator (`_FillValue = NaN`).

| Variable Name | Long Name / Definition | Units | Dimensions | Data Type |
| --- | --- | --- | --- | --- |
| **lon** | Longitude | degrees_east | lon (1440) | double |
| **lat** | Latitude | degrees_north | lat (720) | double |
| **time** | Time | days since 1993-01-01 | time (1) | double |
| **sla** | Sea Level Anomaly | m | lat, lon | double |
| **uadv** | Zonal (u) component of the nonlinear advective term | m/s | lat, lon | double |
| **vadv** | Meridional (v) component of the nonlinear advective term | m/s | lat, lon | double |
| **utotal** | Zonal (u) component of the total flow field (ugeo+uekman+uadv) | m/s | lat, lon | double |
| **vtotal** | Meridional (v) component of the total flow field (vgeo+vekman+vadv) | m/s | lat, lon | double |
| **resu** | Residual of the zonal (u) momentum | m/s2 | lat, lon | double |
| **resv** | Residual of the meridional (v) momentum | m/s2 | lat, lon | double |
| **ugeo** | Zonal (u) component of the geostrophic current | m/s | lat, lon | double |
| **vgeo** | Meridional (v) component of the geostrophic current | m/s | lat, lon | double |
| **uekman** | Zonal (u) component of the surface (0 m) Ekman current | m/s | lat, lon | double |
| **vekman** | Meridional (v) component of the surface (0 m) Ekman current | m/s | lat, lon | double |

---

## 5. Global Metadata

Each NetCDF file contains global attributes to track provenance and creation details:

* `creation_date`: Automatically generated date of file creation.
* `author`: Zhongya Cai and Guangxi Cui et al., University of Macao.
* `Conventions`: CF-1.8

---

## 6. Data Access and Download Method

Due to the large volume of the full 31-year dataset (exceeding 500 GB), which surpasses standard repository upload limits, we have uploaded a representative sample data file alongside the `README.txt` directly to this Zenodo repository.

To access and download the complete dataset, all individual files are hosted on a high-speed remote S3 server.

**Base URL:**

```bash
https://s3.jn1.is.shanhe.com/umdr2026

```

Users can retrieve specific files by appending the standardized directory structure to the Base URL:

```bash
# Download Format
[Base_URL]/[YYYY]/[MM]/[YYYY]_[MM]_[DD].nc

# Download Examples
https://s3.jn1.is.shanhe.com/umdr2026/1993/01/1993_01_01.nc
https://s3.jn1.is.shanhe.com/umdr2026/1993/01/1993_01_02.nc

```
