# Fitbit Fitness & Sleep Data Analysis (Bellabeat Case Study)

An end-to-end data analysis project and interactive web dashboard applying the Google Data Analytics framework (**Ask, Prepare, Process, Analyze, Share, Act**) to smart device tracking data.

---

## 1. Ask Phase
* **Business Task**: Analyze smart device usage data to gain insights into how consumers use non-Bellabeat smart devices and identify growth opportunities for Bellabeat marketing strategies.
* **Key Stakeholders**: Urška Sršen (Co-founder & Chief Creative Officer), Sando Mur (Co-founder & Executive Team Member), and Bellabeat Marketing Analytics Team.
* **Core Questions**:
  1. What are the key trends in smart device usage?
  2. How could these trends apply to Bellabeat customers?
  3. How can these trends help influence Bellabeat marketing strategy?

---

## 2. Prepare Phase
* **Data Source**: Public domain dataset **Fitbit Fitness Tracker Data** (CC0: Public Domain) stored on Kaggle.
* **Dataset Scope**: Contains personal fitness tracker data from 30 eligible Fitbit users, including minute-level output for physical activity, heart rate, and sleep monitoring.
* **Data Organization**: 
  * `dailyActivity_merged.csv` (940 daily records across steps, distance, intensity, and calories).
  * `sleepDay_merged.csv` (413 daily sleep logs including minutes asleep and time in bed).
* **Data Limitations**: Small sample size ($N=30$), potential sample bias, lack of demographic data (age/gender), and limited collection duration (31 days).

---

## 3. Process Phase
Data cleaning, transformation, and integration were executed in Python using `Pandas` inside the `bellabeat.ipynb` notebook:
* **Schema Normalization**: Standardized temporal column names (`ActivityDate` and `SleepDay`) to a unified `Date` key (`datetime64[us]`).
* **Data Merging**: Executed a `left` join on `['Id', 'Date']`, preserving all 940 daily activity records while merging corresponding sleep logs.
* **Missing Value Imputation**: Imputed non-monitored sleep values with population averages (`TotalMinutesAsleep` $\approx$ 419.5 min, `TotalTimeInBed` $\approx$ 458.6 min) to preserve overall row integrity for multi-variable analysis.
* **Feature Engineering**: Created custom metrics including total active time, wear frequency classification, and weekday activity indicators.

---

## 4. Analyze Phase
* **Correlation Analysis**: Demonstrated a strong positive correlation between daily step count and total calories burned, with high-intensity active minutes having the highest weighting per calorie spent.
* **Sedentary vs. Active Distribution**: Discovered that sedentary time accounts for the vast majority ($\approx 81\%$) of logged tracking minutes.
* **User Segmentation**: Classified users into three distinct wear frequency tiers (High, Fair, Low) based on tracking consistency.
* **Temporal Patterns**: Identified notable dips in step counts on specific weekdays (e.g., Sundays), indicating weekly routine shifts.

---

## 5. Share Phase

### Key Visualizations
#### 1. Total Steps vs. Calories Burned
![Total Steps VS Calories Burned](Visualizations/total_steps_vs_calories_burned.png)
* *Insight*: Strong direct relationship between steps and energy expenditure; intensity levels accelerate caloric burn rate.

#### 2. Daily Active Minutes Breakdown
![Daily Active Donut Chart](Visualizations/daily_active_donut_chart.png)
* *Insight*: Highlights the overwhelming dominance of sedentary minutes, pinpointing a need for active habit triggers.

#### 3. Average Steps Taken by Day of the Week
![Average Steps Taken by Day of the Week](Visualizations/average_steps_taken_by_day_of_the_week.png)
* *Insight*: Uncovers specific day-of-week engagement dips to optimize notification timing.

#### 4. User Classification by Wear Frequency
![User Classification by Wear Frequency](Visualizations/user_classification_by_wear_frequency.png)
* *Insight*: Groups users by tracking adherence to evaluate long-term device retention and engagement.

### Interactive Dashboard
Built a interactive web dashboard using **Streamlit** and **Plotly** (`app.py`) featuring dynamic KPI metrics, individual user filtering, and interactive sleep efficiency scatter plots.

---

## 6. Act Phase (Recommendations)
1. **Automated Sedentary Alerts**: Program wellness trackers (e.g., Bellabeat Leaf/Time) to send subtle haptic feedback after 60+ minutes of continuous inactivity.
2. **Personalized Sleep Hygiene Guidance**: Use time-in-bed vs. time-asleep gaps to provide customized bedtime reminders and relaxation notifications.
3. **Targeted Weekend Engagement**: Push motivational challenges on traditionally low-activity days (e.g., Sunday step goals) to maintain weekly consistency.
4. **Gamified Wear Retention**: Reward users in the "Fair" and "Low" wear frequency tiers with loyalty points or streak badges to boost daily device adoption.

---

## Project Structure
```text
├── data/
│   ├── dailyActivity_merged.csv
│   ├── sleepDay_merged.csv
│   └── merged_fitbit_data.csv                  # Processed clean dataset
├── notebooks/
│   └── bellabeat.ipynb                         # Exploratory analysis & data pipeline
├── Visualizations/                             # Saved chart exports
│   ├── average_steps_taken_by_day_of_the_week.png
│   ├── daily_active_donut_chart.png
│   ├── total_steps_vs_calories_burned.png
│   └── user_classification_by_wear_frequency.png
├── app.py                                      # Interactive Streamlit web dashboard
├── requirements.txt                            # Python dependencies
└── README.md
