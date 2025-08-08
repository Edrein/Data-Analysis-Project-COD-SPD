# Data Analysis Project – COD/SPD

# Project Overview
This project analyzes sterilization and kit usage data for the College of Dentistry's Sterile Processing Department (SPD).  
It combines:
- A **Tableau dashboard** for interactive visual exploration.  
- A **Jupyter Notebook** for data cleaning and analysis. 
- Data cleaning and Analysis done via a combination of **Pandas** and **SQLite**.
- A combination of real world data provided by the SPD and simulated data to maintain compliance with regulations.

## Data Dictionary

| Field Name            | Description                                                   | Type                | Allowed Values      | Example                         | Null % | Unique Values | Min | Max | Units | Notes |
|-----------------------|---------------------------------------------------------------|---------------------|---------------------|----------------------------------|--------|---------------|-----|-----|-------|-------|
| Kit                   | Unique identifier for the kit (alphanumeric).                 | string (ID)         |                     | SII21058402N                    |        |               |     |     |       | Stable key used to join kit-level and movement records. |
| Kit Type Description  | Human-readable description of kit type.                       | string (category)   |                     | Bur Block 9 - Temporization     |        |               |     |     |       | Maps to code in 'Kit Type' if a code system exists. |
| Kit Item Cost/Value   | Cost or value of a single item within the kit.                 | float (nullable)    |                     | 2.27                            |        |               |     |     | USD   | Consider rounding to 2 decimals; check whether value is source-estimated or calculated. |
| Item Type             | Category for items within the kit.                            | string (category)   | Bur Block           | Bur Block                       |        |               |     |     |       | Enumerate all item categories for validation in Tableau. |
| Sterilization Method  | Method used to sterilize the kit.                              | string (category)   | Steam               | Steam                           |        |               |     |     |       | List all valid methods (e.g., Steam, EO gas, Dry heat) if applicable. |
| Kit Cost/Value        | Total cost or value of the entire kit.                         | float (nullable)    |                     |                                  |        |               |     |     | USD   | Might be blank in source; confirm whether this is captured or derived. |
| Kit Dispensary        | Dispensary or department responsible for the kit.              | string (nullable)   |                     |                                  |        |               |     |     |       | If controlled list exists, capture allowed location names/codes. |
| Kit Out Of Service    | Indicates whether the kit is out of service.                   | boolean / string    | Y, N                |                                  |        |               |     |     |       | Confirm true/false representation (Y/N vs. 1/0 vs. date of OOS). |
| Kit Type              | Coded kit type identifier.                                     | string (code)       | BBTEMP              | BBTEMP                          |        |               |     |     |       | Code should map to 'Kit Type Description' (maintain a reference table). |
| Kit Location          | Clinic or physical location of the kit at time of event.       | string (category)   | FPC                 | FPC                             |        |               |     |     |       | Maintain a location directory (full name, address) for Tableau tooltips. |
| Kit Date Out          | Calendar date the kit was checked out/used.                    | date                |                     | 2025-01-07                      |        |               |     |     |       | Ensure stored as date (not string) for correct Tableau date functions. |
| Kit Time Out          | Time the kit left the dispensary/stock.                        | time                |                     | 12:15:00                        |        |               |     |     |       | Store as time; combine with 'Kit Date Out' to create a timestamp if needed. |
| Kit Time In           | Time the kit returned to inventory.                            | time                |                     | 20:15:00                        |        |               |     |     |       | If return occurs on a different date, capture 'Kit Date In' or compute using rotation logic. |


**Key insights you can explore:**
- Breakdowns by **Kit Type** and **Sterilization Method**
- Location-based filtering for deeper insight
- Inventory rotation simulated from **Kit Date Out**, **Kit Time In**, and **Kit Time Out**
- Cost analysis with null values removed

---

## Methods to utilize this project

### Option A — Open the Tableau Dashboard (no coding required)
1. Download the packaged workbook:  
   **[SPDDataAnalysis.twbx](Tableau_Project/SPDDataAnalysis.twbx)**
2. Open it in **Tableau Public** (free download: https://public.tableau.com/)
3. Use the filters to explore as you'd like.

---

### Option B — Run the Python analysis locally
1. **Clone the repository**
   ```bash
   git clone https://github.com/Edrein/Data-Analysis-Project-COD-SPD.git
   cd Data-Analysis-Project-COD-SPD
   ```
2. **Install dependencies**
     ```bash
     pip install pandas sqlite3
     ```
3. **Run the notebook**
   - In VS Code: open `notebook.ipynb` and run each cell in order.
   - Or in Jupyter:  
     ```bash
     jupyter notebook
     ```
     Then open `notebook.ipynb`.

---

##  Repository Structure
```
Data-Analysis-Project-COD-SPD/
├─ Tableau_Project/
│  └─ SPDDataAnalysis.twbx       # Tableau dashboard
├─ data/                         # Any supporting data files
├─ database/                     # Any DB or interim files
├─ final_data_v2.xlsx            # Main cleaned dataset with the simulation code
├─ final_data.xlsx               # Original cleaned dataset without the additional simulated code for inventory
├─ notebook.ipynb                # Jupyter Notebook with analysis
└─ README.md                     # Documentation
```

---

## Technologies Used
- **VS Code** — Edit code, run notebooks, and manage the project
- **Jupyter Notebook** — Combine code and explanations for easy understanding
- **Python** — Analyze and clean the raw dataset
  - **Pandas**: Load, clean, and manipulate Excel data
  - **SQLite**: Additional joining of Excel data
- **Tableau Public** — Create interactive dashboards to visualize kit inventory and sterilization data
- **Git & GitHub** — Track changes and share the project

---

## Notes for Reviewers
- If you only want to explore the data visually, open the **Tableau dashboard** — no coding needed.
- If you want to see *how* the data was prepared, read and run the `notebook.ipynb`.
- You can use the `Kit Location` filter to drill down into data for specific clinics.
- The color scheme is based on actual colors used in the SPD department for color coordination of clinic assets.

---