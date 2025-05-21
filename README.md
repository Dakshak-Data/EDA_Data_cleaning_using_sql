# EDA_Data_cleaning_using_sql
# 💻 Laptop Dataset SQL Cleaning Project

This project focuses on cleaning and transforming a raw laptop dataset using SQL. The goal is to prepare the data for analysis by standardizing formats, splitting composite columns, and extracting meaningful features.

## 📁 Dataset
- Raw dataset is assumed to be loaded into a MySQL table named `laptop` inside a database named `Lap`.

## 🧼 Cleaning Steps

### 1. Initial Setup
- Created backup: `laptops_backup`
- Checked row count and memory usage
- Removed non-essential column: `Unnamed: 0`

### 2. Null and Duplicate Handling
- Deleted rows with all fields as NULL
- Removed duplicate rows using `GROUP BY` with `MIN(index)`
- Added `index` column with `AUTO_INCREMENT` for uniqueness

### 3. Column-Specific Cleaning

#### 🔸 `Ram` and `Weight`
- Removed text suffixes like 'GB' and 'kg'
- Converted `Ram` to `INTEGER`
- Converted `Weight` to `DECIMAL`

#### 🔸 `Price`
- Rounded values and cast to `INTEGER`

#### 🔸 `OpSys`
Standardized operating systems:
- `macos`, `windows`, `linux`, `N/A`, `other`

#### 🔸 `Gpu`
- Split into `gpu_brand` and `gpu_name`
- Dropped original `Gpu` column

#### 🔸 `Cpu`
- Extracted `cpu_brand`, `cpu_name`, and `cpu_speed` (GHz)
- Standardized `cpu_name` to only first two tokens
- Dropped original `Cpu` column

#### 🔸 `ScreenResolution`
- Extracted `resolution_width` and `resolution_height`
- Added `touchscreen` column using keyword matching
- Dropped original `ScreenResolution` column

#### 🔸 `Memory`
- Split into `memory_type`, `primary_storage`, and `secondary_storage`
- Converted TB to GB where applicable
- Types included: `SSD`, `HDD`, `Hybrid`, `Flash Storage`

  ## 🛠️ Technologies Used
- MySQL
- SQL (DDL, DML, functions, conditionals)

## 📊 Outcome
Cleaned and structured dataset ready for analysis or machine learning pipelines.

---
