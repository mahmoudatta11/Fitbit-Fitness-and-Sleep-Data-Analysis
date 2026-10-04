# Mahmoud_Portfolio
# Fitbit Fitness & Sleep Data Analysis

An exploratory data analysis (EDA) and interactive web dashboard analyzing daily activity levels, caloric expenditure, and sleep patterns using Python.

## Highlights
- **Integrated Data Sources**: Combined daily tracking metrics (`dailyActivity_merged.csv`) with sleep logs (`sleepDay_merged.csv`) across unique user IDs and dates.
- **Data Hygiene**: Handled datetime conversions, schema alignment, and mean-value imputation for missing sleep tracking days.
- **Interactive Visualization**: Built a Streamlit & Plotly dashboard to analyze user performance, activity distribution, and sleep efficiency.

## Project Structure
```text
├── data/
│   ├── dailyActivity_merged.csv
│   └── sleepDay_merged.csv
├── notebooks/
│   └── fitbit_eda_pipeline.ipynb
├── app.py                  # Streamlit dashboard script
├── merged_fitbit_data.csv  # Processed dataset
├── requirements.txt        # Project dependencies
└── README.md
