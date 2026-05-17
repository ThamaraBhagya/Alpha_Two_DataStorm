# Alpha Two DataStorm: Sales Volume Prediction Pipeline 🚀

This repository contains a comprehensive data engineering and machine learning pipeline designed to predict the **Volume_Liters_Sum** for **January 2026** across various distribution hubs. The project follows a robust **Bronze-Silver-Gold** architecture, ensuring data integrity and scalability from raw ingestion to model-ready features.

---

## 📂 Project Structure

The codebase is organized into three primary layers, reflecting the data evolution process:

### 1. 🥉 Bronze Layer (Raw Data)
The landing zone for all raw datasets in their original format.
- `transactions_history_final.csv`: Raw transactional records.
- `outlet_master.csv`: Baseline outlet metadata.
- `holiday_list.csv`: Raw holiday data.
- `outlet_coordinates.csv`: Geospatial data for POI analysis.

### 2. 🥈 Silver Layer (Cleaned & Augmented)
Data that has been processed, formatted, and enriched.
- **Data Engineering**: 
  - Date orientation and standardized formatting (`YYYY-MM-DD`).
  - Removal of redundant/noisy columns.
  - Handling missing coordinates and distributor mapping.
- **Feature Engineering**:
  - Monthly aggregation of `Volume_Liters_Sum`.
  - Integration of `Distributor_ID`, `Seasonality_Index`, `Outlet_Size`, `Cooler_Count`, and `Outlet_Type`.
  - Holiday count per month integration.

### 3. 🥇 Gold Layer (Model Ready)
Highly specialized datasets categorized by Hub Potential.
- Categorized Hubs: `Low`, `Medium`, `High`, and `Elite` Potential Hubs.
- Time-series optimized formats for monthly volume forecasting.
- POI data is added to the Gold layer.

---

## 🛠️ The Pipeline

### Phase 1: Data Engineering & Cleaning
Located in `dataCleaning.ipynb` and `cleanData_outletSumAnnual.ipynb`.
- **Date Standardization**: Ensuring all temporal data is correctly oriented for time-series analysis.
- **Noise Reduction**: Dropping columns that do not contribute to predictive power.
- **Distributor Mapping**: Resolving relationships between outlets and distributors.

### Phase 2: Feature Engineering
Handled across multiple notebooks including `distributorAdding.ipynb` and `POI_data_classification.ipynb`.
- **Temporal Features**: Calculating total monthly volume and annual aggregates for 2023, 2024, and 2025.
- **Contextual Features**: Adding seasonality indices and holiday frequency to capture periodic demand spikes.
- **Metadata Integration**: Enriching data with outlet-specific attributes (Size, Cooler Count, Type).

### Phase 3: Hub Categorization
The dataset is segmented into four distinct categories based on historical performance and potential:
- **Low Potential Hubs**
- **Medium Potential Hubs**
- **High Potential Hubs**
- **Elite Potential Hubs**

### Phase 4: Modeling & Prediction
Implemented in the `modal_pipline_*.ipynb` suite.
- Separate analytical pipelines for each category to capture specific variance.
- Models are trained on 2023–2025 data to predict the expected volume for **January 2026**.
- **Final Output**: `All_Predictions_2026_01.csv` containing the unified forecast.

---

## 🚀 Getting Started

To reproduce the results, follow the execution order of the Jupyter Notebooks:

1.  **Data Ingestion**: Run `dataCleaning.ipynb` to prepare the Silver layer.
2.  **Feature Enrichment**: Run `distributorAdding.ipynb` and `POI_data_classification.ipynb`.
3.  **Classification**: Run `outletClassification.ForModel.ipynb` to generate category-specific Gold datasets.
4.  **Training & Inference**: Execute the `modal_pipline_*.ipynb` notebooks for each category (Elite, High, Medium, Low).

---

## 📊 Analytical Insights

- **EDA**: Initial exploratory data analysis was performed to identify seasonality patterns and distributor performance.
- **POI Analysis**: External data scraping was used to enrich the "Potential" classification of hubs.
- **Multi-Model Approach**: Instead of a one-size-fits-all model, we utilize category-specific architectures to handle the high variance between Elite and Low potential hubs.

---

Developed for **Data Storm 1st Round** | Alpha Two Team
