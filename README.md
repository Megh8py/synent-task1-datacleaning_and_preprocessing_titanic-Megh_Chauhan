#  Task 1: Data Cleaning & Preprocessing – Titanic Dataset

> Synent Technologies Data Science Internship

---

##  Problem Statement

Real-world datasets are messy — they contain missing values, inconsistent data types, duplicate records, and poorly named columns. This project focuses on cleaning and preprocessing the Titanic dataset to make it fully ready for analysis or machine learning.

---

##  Dataset Details

| Property | Details |
|----------|---------|
| **Name** | Titanic Dataset |
| **Source** | [Kaggle – Titanic Competition](https://www.kaggle.com/competitions/titanic/data) |
| **Rows** | 891 |
| **Columns** | 12 (original) → 16 (after feature engineering) |
| **Target Column** | `survived` (0 = No, 1 = Yes) |

### Key Columns
| Column | Description |
|--------|-------------|
| `survived` | Survival status (0 = No, 1 = Yes) |
| `pclass` | Passenger class (1st, 2nd, 3rd) |
| `sex` | Gender |
| `age` | Age in years |
| `sibsp` | No. of siblings/spouses aboard |
| `parch` | No. of parents/children aboard |
| `fare` | Ticket fare |
| `embarked` | Port of embarkation (C, Q, S) |

---

##  Approach

### Step 1 – Initial Exploration
- Checked dataset shape, data types, and summary statistics
- Visualized missing values using a heatmap

### Step 2 – Handle Missing Values
| Column | Missing % | Strategy |
|--------|-----------|----------|
| `age` | ~20% | Filled with median grouped by class + sex |
| `embarked` | ~0.2% | Filled with mode |
| `deck` / `cabin` | >77% | Dropped entirely |

### Step 3 – Remove Duplicates
- Checked for and removed any duplicate rows

### Step 4 – Convert Data Types
- Converted `pclass`, `sex`, `embarked` to `category`
- Ensured `age` and `fare` are `float`
- Converted `survived` to `int`

### Step 5 – Rename Columns
- Renamed to readable, descriptive snake_case names
  - `sibsp` → `siblings_spouses`
  - `parch` → `parents_children`
  - `embarked` → `embarkation_port`

### Step 6 – Feature Engineering
| New Feature | Description |
|-------------|-------------|
| `family_size` | `siblings_spouses + parents_children + 1` |
| `is_alone` | 1 if travelling alone, 0 otherwise |
| `age_group` | Binned into Child / Teen / Young Adult / Adult / Senior |
| `fare_tier` | Quartile-based fare category (Low / Medium / High / Very High) |

### Step 7 – Encode Categorical Variables
- `sex` → `sex_encoded` (Male=0, Female=1)
- `embarkation_port` → `port_encoded` (S=0, C=1, Q=2)

---

##  Results & Key Findings

- **Female survival rate (~74%)** was far higher than male (~19%)
- **1st class passengers** had the highest survival rate (~63%)
- **Children (age < 12)** showed relatively higher survival rates
- **Fare and survival** are positively correlated
- Final clean dataset has **0 missing values** and **0 duplicates**
- Dataset is now fully ready for EDA or ML modeling

### Visualizations Generated
- Missing value heatmap
- Survival rate by gender (bar chart)
- Survival rate by passenger class (bar chart)
- Age distribution by survival (histogram)
- Fare distribution by class (boxplot)
- Correlation heatmap

---

##  Repository Structure

```
synent-task1-datacleaning-yourname/
│
├── task1_titanic_data_cleaning.ipynb   # Main notebook
├── train.csv                           # Raw dataset (or link below)
├── titanic_cleaned.csv                 # Output: clean dataset
└── README.md                           # This file
```

---

##  How to Run

1. Clone this repository
   ```bash
   git clone https://github.com/yourusername/synent-task1-datacleaning-yourname.git
   ```
2. Install dependencies
   ```bash
   pip install pandas numpy matplotlib seaborn
   ```
3. Open the notebook
   ```bash
   jupyter notebook task1_titanic_data_cleaning.ipynb
   ```
4. Run all cells top to bottom

> **Note:** If you don't have `train.csv`, the notebook uses seaborn's built-in Titanic loader automatically.

---

##  Tools & Libraries

| Tool | Purpose |
|------|---------|
| Python 3.x | Programming language |
| Pandas | Data manipulation |
| NumPy | Numerical operations |
| Matplotlib | Visualizations |
| Seaborn | Statistical visualizations |
| Jupyter Notebook | Development environment |

---

##  Author

Megh Chauhan

Data Science Intern – Synent Technologies  
