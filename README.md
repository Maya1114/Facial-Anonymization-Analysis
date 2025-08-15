# 👥 Face Anonymization Fairness Evaluation

This project evaluates the fairness and performance of a face anonymization system across gender and race attributes using statistical analysis. The goal is to assess whether the anonymization process disproportionately affects certain demographic groups.

---

## 📊 Dataset Description

The dataset used in this project consists of predictions from a face attribute classifier before and after applying anonymization techniques. Each CSV file includes:

- `dominant_gender`: Gender predicted before anonymization  
- `dominant_race`: Race predicted before anonymization  
- `anonymized_dominant_gender`: Gender predicted after anonymization  
- `anonymized_dominant_race`: Race predicted after anonymization  
- `dominant_gender_diff`: 1 if gender prediction remained the same after anonymization, else 0  
- `dominant_race_diff`: 1 if race prediction remained the same after anonymization, else 0  

---

## 🧮 What the Code Does

### 1. **Combines Results**
All CSV files are merged into a single DataFrame for comprehensive analysis.

### 2. **Statistical Parity Analysis**
- Calculates average accuracy of gender predictions for:
  - Women (unprivileged group)
  - Men (privileged group)

- Calculates average race prediction accuracy across:
  - Asian
  - Black
  - Indian
  - Middle Eastern
  - Latino Hispanic
  - White

### 3. **Intersectional Fairness**
Analyzes prediction accuracy based on **intersectional subgroups** (e.g., Woman + Asian, Man + Black).

- Separate evaluations are done for:
  - Gender prediction accuracy (`dominant_gender_diff`)
  - Race prediction accuracy (`dominant_race_diff`)

### 4. **Distribution Comparison**
- Compares the distributions of gender and race **before and after** anonymization.

---

## 📈 Sample Output Summary

### 🔹 Gender Accuracy (Intersectional)

| Gender | Race            | Accuracy (%) |
|--------|------------------|--------------|
| Man    | Asian            | 96.31%       |
| Woman  | Asian            | 44.87%       |
| Man    | Black            | 98.41%       |
| Woman  | Black            | 53.90%       |
| ...    | ...              | ...          |

### 🔹 Race Accuracy (Intersectional)

| Gender | Race            | Accuracy (%) |
|--------|------------------|--------------|
| Man    | White            | 73.71%       |
| Woman  | Indian           | 30.37%       |
| ...    | ...              | ...          |

### 🔹 Distribution Before vs After Anonymization

#### Gender

| Gender | Original | Anonymized |
|--------|----------|------------|
| Man    | 8507     | 9579       |
| Woman  | 2467     | 1395       |

#### Race

| Race             | Original | Anonymized |
|------------------|----------|------------|
| White            | 3238     | 3349       |
| Asian            | 2848     | 2738       |
| Black            | 2030     | 2500       |
| Latino Hispanic  | 1237     | 988        |
| Middle Eastern   | 940      | 876        |
| Indian           | 681      | 523        |

---

## 📌 Key Insights

- The anonymization process tends to reduce gender prediction accuracy **more for women** than for men.
- Some racial groups (e.g., Indian, Latino Hispanic) show **significant drops** in prediction consistency post-anonymization.
- Distributions also shift after anonymization, suggesting some demographic characteristics are altered more than others.

---

## 🛠️ Technologies Used

- Python 3  
- Pandas  
- Google Colab  
- `tabulate` (for display formatting)

---

## 📁 How to Run

1. Clone the repository or open the notebook in Google Colab.
2. Make sure the dataset (`results1.csv` to `results11.csv`) is available in your Google Drive path.
3. Run all cells to view:
   - Statistical parity analysis
   - Intersectional accuracy
   - Distributions before vs after anonymization

---

## 🧠 Citation / Inspiration

This project is inspired by fairness evaluation practices in machine learning and face recognition research. For theoretical background, consider referencing:

- [Fairness and Machine Learning](https://fairmlbook.org/)  
- Papers from conferences like NeurIPS, ICML, and CVPR related to fairness and facial recognition

