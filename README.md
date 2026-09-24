# ApexPlanet Data Analytics — Task 1
## Data Immersion & Wrangling

This repository contains my submission for **Task 1: Data Immersion & Wrangling** in the ApexPlanet Data Analytics internship program.

### Objective

The objective of this task is to acquire, understand, assess, clean, transform, and prepare the provided dataset for analysis.

### Task Coverage

This project covers the three areas specified in the task:

1. **Data Access & Familiarization**
   - Loaded the provided sales dataset.
   - Inspected its structure, columns, data types, and sample records.
   - Created a data dictionary documenting each variable and its business relevance.

2. **Data Quality Assessment**
   - Checked dataset dimensions.
   - Checked data types.
   - Identified missing values.
   - Checked for duplicate rows.
   - Validated date values.
   - Reviewed numerical ranges.
   - Validated `Total_Sales` against `Quantity × Unit_Price`.

3. **Data Cleaning & Transformation**
   - Standardized `Order_Date` to datetime.
   - Filled missing `Age` values using the median.
   - Filled missing `City` values with `Unknown`.
   - Removed duplicate rows.
   - Created an `Age_Group` feature for downstream analysis.
   - Exported an analysis-ready cleaned dataset.

## Repository Structure

```text
ApexPlanet_Task01_GitHub/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── notebooks/
│   └── Task01_Data_Immersion_Wrangling.ipynb
│
├── src/
│   └── clean_data.py
│
├── data/
│   ├── raw/
│   │   └── ApexPlanet_DataAnalytics_Dataset.xlsx
│   │
│   └── processed/
│       └── ApexPlanet_Task01_Cleaned_Dataset.csv
│
└── docs/
    ├── data_dictionary.md
    └── raw_data_notes.md
```

> **Dataset note:** The provided internship dataset is not redistributed in this repository by default. Place the original `ApexPlanet_DataAnalytics_Dataset.xlsx` inside `data/raw/` before running the notebook or script, subject to the internship's sharing/GitHub rules.

## Dataset

The dataset contains the following variables:

| Column | Description |
|---|---|
| `Order_ID` | Unique identifier for each order |
| `Order_Date` | Date on which the order was placed |
| `Customer_ID` | Unique customer identifier |
| `Customer_Name` | Customer name/label |
| `Age` | Customer age |
| `Gender` | Customer gender |
| `City` | Customer/order city |
| `Product` | Purchased product |
| `Category` | Product category |
| `Quantity` | Number of units purchased |
| `Unit_Price` | Price per unit |
| `Total_Sales` | Total value of the order |

## Key Data Quality Findings

The initial profiling of the provided dataset found:

- **1,000 rows** and **12 original columns**
- **20 missing values** in `Age`
- **13 missing values** in `City`
- **0 duplicate rows**
- `Order_Date` initially stored as text and converted to datetime
- `Total_Sales` validated against `Quantity × Unit_Price`
- No sales-calculation mismatches were found during validation

## Cleaning Decisions

### Missing Age
Missing ages were replaced with the **median age** of the available records. This avoids dropping otherwise usable transaction records and is less sensitive to extreme values than the mean.

### Missing City
Missing city values were replaced with **`Unknown`** rather than assigning a city without evidence.

### Duplicate Records
No duplicate rows were found. The cleaning script still includes a duplicate-removal step so the workflow is robust and reproducible.

### Age Group
An `Age_Group` field was created for future demographic analysis.

## How to Run

### 1. Install dependencies

```bash
pip install -r requirements.txt
```

### 2. Add the source dataset

Place:

```text
ApexPlanet_DataAnalytics_Dataset.xlsx
```

inside:

```text
data/raw/
```

### 3. Run the notebook

Open:

```text
notebooks/Task01_Data_Immersion_Wrangling.ipynb
```

and run all cells from top to bottom.

### 4. Or run the cleaning script

From the repository root:

```bash
python src/clean_data.py
```

The cleaned dataset will be written to:

```text
data/processed/ApexPlanet_Task01_Cleaned_Dataset.csv
```

## Deliverables

This repository is organized around the Task 1 deliverables:

- Data dictionary
- Data quality assessment
- Cleaning/transformation code
- Analysis-ready cleaned dataset
- Jupyter Notebook documenting the workflow

## Tools Used

- Python
- Pandas
- Jupyter Notebook
- OpenPyXL

## Author

**Tripurari Kumar**

Data Analytics Intern
