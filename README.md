# Distributed Generation Data Loader


## 📌 Project Overview

This repository consolidates data pipelines that handle various aspects of Brazil’s distributed energy generation ecosystem. The datasets are sourced from ANEEL and are pre-processed using Python scripts, then loaded into Oracle tables using SQL inserts and batch operations.

---

## 📂 Project Structure

### 1. **Python Scripts for Data Ingestion**
Each script processes a specific type of GD dataset:

- `GD_Aplicacao_20230518.py`: Processes the application forms of distributed generation units.
- `GD_empreedimentos_ANEEL_20230801.py`: Processes data about energy generation projects registered with ANEEL.
- `GD_samp_ANEEL_20230817.py`: Loads consolidated statistical data of GD units.
- `GD_samp_balanco_ANEEL_20230807.py`: Handles energy balance data from ANEEL reports.
- `GD_subsidios_ANEEL_20230620.py`: Loads data on public subsidies granted to GD projects.
- `GD_tarifas_ANEEL_20230620.py`: Ingests updated tariff data per distribution concession.
- `GD_UCsPorMunicipio_20230720.py`: Loads data about consumer units (UCs) per municipality.

Each script follows a standard structure:
- Download/parse .CSV or Excel files from ANEEL sources
- Clean and transform data (drop missing fields, type conversion, normalization)
- Connect to Oracle database using `cx_Oracle`
- Batch insert into staging or final tables

---

### 2. **Static SQL Scripts**

#### `GD_FATOR_IRRADIACAO.sql`
Contains hardcoded irradiation indices per electricity distributor. These values are static and do not require periodic update scripts.

#### `GD_Fator_Capacidade.sql`
Stores capacity factor values by energy source type (e.g., solar, wind, thermal). These are constants used in performance estimates and do not require automation.

---

### 3. **Database Schema**

SQL scripts include:
- `Tabela_Oracle.sql`: Table creation statements and structure definitions for storing the processed datasets. Ensures the data model aligns with ANEEL’s regulatory reporting.

---

## 🧠 Features

- ✅ Automates parsing and transformation of multiple ANEEL datasets
- ✅ Inserts processed data into Oracle tables
- ✅ Modular design to enable updates or replacements of individual scripts
- ✅ SQL insert scripts for static reference tables
- ✅ Handles encoding, type mismatch, and column inconsistencies

---

## 💻 Technologies Used

- Python 3.x
- Pandas
- cx_Oracle
- Oracle SQL
- ANEEL public datasets

---

## 📊 Use Cases

- Regulatory reporting and compliance
- Market intelligence and distributed generation statistics
- Business analysis of GD subsidies, tariffs, and energy balances

---

## 🚀 How to Use

1. Ensure Python and Oracle client libraries are installed.
2. Configure Oracle connection credentials.
3. Run individual Python scripts for each dataset:
   ```bash
   python GD_samp_ANEEL_20230817.py
   ```
4. Run SQL scripts for static tables via Oracle SQL Developer or CLI:
   ```sql
   @GD_FATOR_IRRADIACAO.sql
   ```

---

## 📁 Data Sources

All datasets are publicly available on the ANEEL website (https://www.aneel.gov.br/)


