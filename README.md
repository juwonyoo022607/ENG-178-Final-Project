# ENG-178-Final-Project

# to do by thrusday

# Athlete Overtraining Data Analysis

Exploratory data analysis of a dataset of 600 athletes, looking at which training, recovery and physiological factors are linked to overtraining. The script generates a 7-page PDF summary report.

## Dataset

`data.csv` has 600 rows and 16 numeric columns.

| Group | Columns |
|---|---|
| Training load | `TrainingHoursPerWeek`, `TrainingIntensity`, `TrainingLoadVariation` |
| Recovery | `RestHoursPerWeek`, `SleepQualityScore`, `MoodScore`, `NutritionScore` |
| Physiology | `HeartRateRest`, `HeartRateVar`, `CortisolLevel`, `TestosteroneLevel`, `CKLevel`, `ReactionTime` |
| Background | `Age`, `InjuryHistory` |
| **Target** | `Overtraining` (0 = No, 1 = Yes) |

- No missing values and no duplicate rows
- Class balance: 360 not overtrained (60%), 240 overtrained (40%)

## Key findings

- **Workload and recovery matter most.** Overtrained athletes average about 22.3 training hours per week versus 16.0 for the rest, and about 24.6 rest hours versus 33.8.
- **Strongest correlations with `Overtraining`:**
  - `TrainingHoursPerWeek` (+0.53)
  - `RestHoursPerWeek` (-0.47)
  - `TrainingIntensity` (+0.26)
  - `SleepQualityScore` (-0.17)
- **Biomarkers show little signal.** Cortisol, testosterone, CK level and heart rate have near-zero linear correlation with the target.
- **Classes are moderately imbalanced,** so accuracy alone would be misleading in a model. Use precision, recall or F1 as well.

## What the report contains

1. Overview and key findings
2. Column types
3. Descriptive statistics
4. Feature means by overtraining status, and class balance
5. Histograms of all columns
6. Boxplots of each feature split by target
7. Correlation heatmap and feature-vs-target correlations

## Getting started

### Requirements

- Python 3.9+
- pandas, numpy, matplotlib, Pillow, reportlab

```bash
pip install pandas numpy matplotlib pillow reportlab
```

### Run

Put `data.csv` in the same folder as the script, then run:

```bash
python summary_report.py
```

This prints a quick profile to the console and writes `summary_report.pdf` to the same folder.

To run it in a Jupyter notebook, paste the script into a cell instead.

## Project structure

```
.
├── data.csv              # dataset
├── summary_report.py     # analysis and PDF generation
├── summary_report.pdf    # generated report
└── README.md
```

## Possible next steps

- Train a classifier (logistic regression, random forest) to predict `Overtraining`
- Check feature importance and interactions, for example training hours against rest hours
- Handle class imbalance with class weights or resampling
