# 🚀 ClearML Data Migration: `<Source Environment>` ➔ `<Target Environment>`

This repository provides a guide on what data and configurations can be migrated from `<Source Environment>` to `<Target Environment>` and outlines any limitations on data that will not be updated post-migration.

## 📋 Table of Contents
1. [Overview](#overview)
2. [Migratable Data](#migratable-data)
3. [Data that will not be migrated](#data-that-will-not-be-migrated)
4. [Data that will not be updated Post-Migration](#data-that-will-not-be-updated-post-migration)

---

## 📌 Overview
This guide assists teams in understanding the ClearML migration scope, highlighting the data that can be migrated from `<Source Environment>` to `<Target Environment>`, as well as the elements that will not be updated post-migration.

## ✅ Migratable Data
The following ClearML data and configurations **will** be successfully migrated from `<Source Environment>` to `<Target Environment>`:

- **Datasets, Tasks & Pipelines**: ClearML-managed datasets, Tasks & Pipelines with the following statuses will be migrated: **created, in_progress, stopped, closed, failed, completed, queued, published, publishing,** and **unknown**. The migration will include metadata under all relevant tabs, except where noted in the "Data that will not be migrated" section:
  - Execution
  - Configuration
  - Artifacts
  - Dataview
  - Info
  - Console
  - Scalar
  - Plots
  - Debug samples
  
- **S3 Data**: If files inside your S3 bucket are too large to be transferred, you can approach Jovan from AI-Engineering Cluster to perform backend transfer of data from `<Source Environment>` ➔ `<Target Environment>` on your behalf.  
  **⚠️ Please note that the file structure of the folder [E.g: clearml-data/ProjectA/published-train-mnist-2.2bb892d3fe154e19bdd43209b0e09d1a/models/mnist.pt] must remain unchanged during this process.**
  
- **Fileserver Data**: Data stored in fileserver will be migrated over and stored in the S3 of `<Target Environment>`. [To be confirmed]
  
- **Artifacts URLs (e.g., models), debug images' URLs, and hyper datasets' frames' URLs**: Links / URLs will be updated as part of the migration process.

## ❌ Data that will not be migrated
Certain components of ClearML data will **not** be migrated to `<Target Environment>`:

- **Datasets**: Specifically, the **destination** data under the **Execution** tab and the **status reason** under the **Info** tab for datasets will not be migrated.
- **Tasks**: Specifically, the **destination** data under the **Execution** tab and the following items under the **Info** tab for Tasks will not be migrated:
  - **Status reason**
  - **Status message**
  - **Queue**
- **Pipelines**: The **status reason** under the **Info** tab for Pipelines will not be migrated.

## ⚠️ Data that will not be updated Post-Migration
Certain ClearML components **will not be updated** after migration and retain their original values:

- **Console Log URLs**: While console logs can be migrated, the URLs within these logs will not be updated to reflect the correct links in `<Target Environment>`.

---

Thank you for giving this a read! ✨
