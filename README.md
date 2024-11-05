# 🚀 ClearML Data Migration: `<Source Environment>` ➔ `<Target Environment>`

This repository provides a guide on what data and configurations can be migrated from `<Source Environment>` to `<Target Environment>` and outlines any limitations on data that will not be updated post-migration.

## 📋 Table of Contents
1. [Overview](#overview)
2. [Data that will be migrated](##data-that-will-be-migrated)
3. [Data that will not be migrated](##data-that-will-not-be-migrated)

---

## 📌 Overview
This guide assists teams in understanding the ClearML migration scope, highlighting the data that can be migrated from `<Source Environment>` to `<Target Environment>`, as well as the elements that will not be updated post-migration.

## ✅ Data that will be migrated
The following ClearML data and configurations **will** be successfully migrated from `<Source Environment>` to `<Target Environment>`:

- **Datasets, Tasks & Pipelines**: ClearML-managed datasets, Tasks & Pipelines with the following statuses will be migrated: **created, in_progress, ~~stopped~~, ~~closed~~, ~~failed~~, completed, ~~queued~~, published, publishing,** and ~~**unknown**~~. The migration will include metadata under the following tabs, except where noted in the "Data that will not be migrated" section:
  - Execution
  - Configuration
  - Artifacts
  - Dataview
  - Info
  - Console
  - Scalar
  - Plots
  - Debug samples
  
- **S3 Data**:  
  1. PMT needs be clear on what data they wish to migrate and export their S3 data from `<Source Environment>` into a zipped folder. (If PMT needs, PMT can get bash script to perform S3 export from Jovan from AI-Engineering Cluster)
  2. PMT copy the zipped folder into a FG / Diskcrypt of the correct data security label and conduct SEP scanning for these files at L12.
  3. PMT transfer the zipped folder into their `<Target Environment>` VDI.
  4. PMT import their S3 data into `<Target Environment>` S3. (If PMT needs, PMT can get bash script to perform S3 import from Jovan from AI-Engineering Cluster)
  5. PMT may generate md5 checksums of their folder after step i, ii and iii to verify data integrity against unintentional corruption during copying and pasting.
  6. If PMT's folder in `<Source Environment>`'s S3 bucket is too large to be transferred, PMT can approach Jovan from AI-Engineering Cluster to perform backend transfer of data from `<Source Environment>` ➔ `<Target Environment>` to complete step iii after they have completed step ii.
  7. **Please note that the file structure of the folder [E.g: ```clearml-data/ProjectA/published-train-mnist-2.2bb892d3fe154e19bdd43209b0e09d1a/models/mnist.pt```] must remain unchanged during this process.**
  
- **Fileserver Data**: Data stored in fileserver will be migrated over and stored in the S3 of `<Target Environment>`. [To be confirmed]
  
- **Artifacts URLs (e.g., models), debug images' URLs, and hyper datasets' frames' URLs** will be updated as part of the migration process.

## ❌ Data that will not be migrated
Certain components of ClearML data will **not** be migrated to `<Target Environment>`:
- **Datasets**:
  - **Execution** Tab
    - **Destination**
  - **Info** Tab
    - **Status Reason**
- **Tasks**:
  - **Execution** Tab
    - **Destination**
  - **Info** tab
    - **Status Reason**
    - **Status Message**
    - **Queue**
- **Pipelines**:
  - **Info**
    - **Status Reason**

- **Console Log URLs**: While console logs can be migrated, the URLs within these logs will retain their orignal values from `<Source Environment>` and not be updated to reflect the correct links in `<Target Environment>`.

---

Thank you for giving this a read! ✨
