# Data Analysis Project – COD/SPD

# Project Overview
This project analyzes sterilization and kit usage data for the College of Dentistry's Sterile Processing Department (SPD).  
It combines:
- A **Tableau dashboard** for interactive visual exploration.  
- A **Jupyter Notebook** for data cleaning and analysis. 
- Data cleaning and Analysis done via a combination of **Pandas** and **SQLite**.

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

---