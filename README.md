# 🧠 Acetylcholinesterase Inhibitor Bioactivity & Descriptor Analysis | ChEMBL + Python

This project presents a cheminformatics pipeline for analyzing bioactivity data on **acetylcholinesterase inhibitors** using the ChEMBL database. It includes comprehensive **data wrangling, descriptor generation, bioactivity classification, pIC50 transformation**, and **statistical evaluation** using Lipinski's rules.

---

## 🎯 Objective

To curate and analyze inhibitor data for acetylcholinesterase from ChEMBL, transform the data for ML tasks, compute molecular descriptors, and explore structure–bioactivity relationships using statistical tests and visualizations.

---

## 📚 Dataset

- **Source**: ChEMBL bioactivity data
- **Target**: Acetylcholinesterase
- **Data Types**: IC50
- **Samples**: ~6,157 molecules → final ML-ready set: **4,620 molecules (2-class)**

---

## 🛠️ Tools & Libraries

- Python: `pandas`, `numpy`, `seaborn`, `matplotlib`, `scipy`
- Molecular descriptors: Lipinski Rule of 5 (MW, LogP, H-bond donors & acceptors)

---

## 🔄 Pipeline Summary

### 🧹 1. Data Curation
- Loaded and cleaned ChEMBL bioactivity data
- Removed invalid or missing entries
- Filtered for IC50 values and consistent units (nM)
- Defined bioactivity classes based on IC50 thresholds:
  - `Active`: ≤ 1000 nM
  - `Inactive`: ≥ 10,000 nM
  - `Intermediate`: excluded from final model

### ⚗️ 2. Descriptor Generation
- Calculated Lipinski descriptors:
  - Molecular Weight (MW)
  - LogP
  - NumHDonors
  - NumHAcceptors

### 🧪 3. Label Engineering & Transformation
- Normalized IC50 values
- Transformed to pIC50: `−log10(IC50 in M)`
- Replaced infinite values from log transformation
- Saved 2-class dataset with SMILES + descriptors + pIC50

### 📊 4. Exploratory Data Analysis
- Frequency plots of active/inactive classes
- Scatter plot: MW vs LogP (colored by class, sized by pIC50)
- Box plots: pIC50, MW, LogP, H-bond donors/acceptors across classes

### 📈 5. Statistical Testing
- **Mann-Whitney U Test** for:
  - pIC50
  - MW
  - LogP
  - NumHDonors
  - NumHAcceptors  
- All showed statistically significant differences between actives and inactives

---

## 📂 Output Files

| File | Description |
|------|-------------|
| `acetylcholinesterase_01_bioactivity_data_raw.csv` | Raw ChEMBL input |
| `acetylcholinesterase_02_bioactivity_data_preprocessed.csv` | Cleaned dataset |
| `acetylcholinesterase_03_bioactivity_data_curated.csv` | Curated IC50 entries |
| `acetylcholinesterase_04_bioactivity_data_3class_pIC50.csv` | pIC50 (3-class) |
| `acetylcholinesterase_05_bioactivity_data_2class_pIC50.csv` | Final ML-ready (2-class) |
| `*.pdf` | Plots (class dist, MW vs LogP, boxplots) |
| `mannwhitneyu_*.csv` | Statistical test results |

---

## 📊 Key Visuals

- `plot_bioactivity_class.pdf`  
- `plot_MW_vs_LogP.pdf`  
- `plot_ic50.pdf`  
- `plot_MW.pdf`, `plot_LogP.pdf`  
- `plot_NumHDonors.pdf`, `plot_NumHAcceptors.pdf`

---

## 🧠 Skills Demonstrated

- Cheminformatics & Drug Discovery Analytics  
- Bioactivity Classification  
- pIC50 Conversion & Label Engineering  
- Lipinski Rule Descriptor Analysis  
- EDA with Statistical Hypothesis Testing  
- Data Export & Reproducibility

---

## 📦 Repository Structure

```bash
📦acetylcholinesterase-cheminformatics
 ┣ 📄 acetylcholinesterase_01_bioactivity_data_raw.csv
 ┣ 📄 acetylcholinesterase_05_bioactivity_data_2class_pIC50.csv
 ┣ 📄 plot_bioactivity_class.pdf
 ┣ 📄 mannwhitneyu_LogP.csv
 ┗ 📄 README.md
