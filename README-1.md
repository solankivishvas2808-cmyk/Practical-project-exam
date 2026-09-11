# 🏃 Personal Fitness Tracker Dashboard

> A clean, object-oriented Python fitness analytics application for tracking activities, validating user input, analyzing performance, and visualizing fitness data.

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458)
![NumPy](https://img.shields.io/badge/NumPy-Numerical%20Computing-013243)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557C)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-4C72B0)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626)

---

## 📌 Overview

**Personal Fitness Tracker Dashboard** is a Python-based data analytics project that converts a simple fitness activity CSV file into an interactive tracking and reporting system.

The application uses an object-oriented `FitnessTracker` class to:

- Load and clean fitness records
- Validate activity entries
- Store new activities
- Calculate fitness metrics
- Filter records by activity and date
- Generate analytical reports
- Visualize activity performance and trends
- Handle invalid input and empty datasets safely

The project is implemented as a Jupyter Notebook and uses CSV as lightweight persistent storage.

---

## ✨ Features

| Feature | Description |
|---|---|
| 📥 Data Loading | Reads fitness records from CSV |
| 🧹 Data Cleaning | Converts data types and removes invalid records |
| ➕ Activity Logging | Adds new activities interactively |
| ✅ Validation | Rejects invalid activities, dates, duration, and calories |
| 📊 Metrics | Calculates duration, calories, frequency, and calorie efficiency |
| 🔎 Filtering | Filters by activity type and date range |
| 📈 Visualization | Creates charts for duration, calories, distribution, and relationships |
| 💾 Persistence | Saves newly logged activities back to CSV |
| 🧪 Testing | Includes validation and edge-case checks |
| 🖥️ Dashboard | Provides a simple interactive menu |

---

## 🛠️ Tech Stack

- **Python** — application logic
- **Pandas** — data loading, cleaning, grouping, filtering, and aggregation
- **NumPy** — numerical calculations
- **Matplotlib** — charts and trend visualization
- **Seaborn** — statistical visualization
- **Jupyter Notebook** — interactive development and dashboard execution
- **CSV** — local data persistence

---

## 📂 Project Structure

```text
Personal-Fitness-Tracker/
│
├── Personal_Fitness_Tracker_Dashboard.ipynb
├── fitness_activities.csv
├── README.md
│
└── charts/
    ├── duration_by_activity.png
    ├── calories_over_time.png
    ├── activity_distribution.png
    └── duration_vs_calories.png
```

---

## 📋 Dataset

The project uses `fitness_activities.csv`.

### Schema

| Column | Type | Description |
|---|---|---|
| `Date` | Date | Date of the fitness session |
| `Activity Type` | String | Exercise category |
| `Duration` | Numeric | Activity duration in minutes |
| `Calories Burned` | Numeric | Recorded calories burned |

### Supported Activities

- 🏃 Running
- 🚶 Walking
- 🚴 Cycling
- 🧘 Yoga
- 🏋️ Strength Training

The supplied dataset contains **15 records** covering **September 1–15, 2026**.

---

## 📊 Dashboard Metrics

The application calculates the following core metrics:

### Total Calories Burned

Sum of all recorded calories:

**4,855 calories**

### Total Activity Duration

Total recorded exercise time:

**680 minutes**

### Average Session Duration

Average duration per activity:

**45.3 minutes**

### Overall Calorie Rate

Calories burned per recorded activity minute:

**7.14 calories/minute**

### Activity Frequency

| Activity | Sessions |
|---|---:|
| Running | 4 |
| Cycling | 3 |
| Walking | 3 |
| Yoga | 3 |
| Strength Training | 2 |

---

## 🔬 Activity-Level Analysis

The notebook groups records by activity and calculates:

- Number of sessions
- Total duration
- Total calories
- Average duration
- Average calories
- Average calories per minute

### Recorded Results

| Activity | Sessions | Total Minutes | Total Calories | Avg. Minutes | Avg. Calories | Avg. Cal/Min |
|---|---:|---:|---:|---:|---:|---:|
| Running | 4 | 150 | 1,540 | 37.50 | 385.00 | 10.30 |
| Cycling | 3 | 155 | 1,310 | 51.67 | 436.67 | 8.47 |
| Strength Training | 2 | 105 | 790 | 52.50 | 395.00 | 7.53 |
| Walking | 3 | 145 | 695 | 48.33 | 231.67 | 4.79 |
| Yoga | 3 | 125 | 520 | 41.67 | 173.33 | 4.18 |

> The calorie figures are values contained in the project dataset and should be treated as recorded estimates rather than medical measurements.

---

## 🧱 Application Architecture

The core logic is encapsulated in the `FitnessTracker` class.

### Main Methods

```python
load_data()
clean_data()
log_activity()
save_data()
calculate_metrics()
filter_activities()
generate_report()
```

### Data Flow

```text
fitness_activities.csv
        │
        ▼
   Load Dataset
        │
        ▼
  Validate & Clean
        │
        ▼
 FitnessTracker
        │
   ┌────┼─────────────┐
   ▼    ▼             ▼
Metrics Filters   Visualizations
   │    │             │
   └────┼─────────────┘
        ▼
   Fitness Report
```

---

## 🧹 Data Cleaning

Before analysis, the application:

1. Verifies required columns.
2. Converts `Date` to a Pandas datetime type.
3. Converts `Duration` to numeric values.
4. Converts `Calories Burned` to numeric values.
5. Removes missing required values.
6. Removes records where duration or calories are `<= 0`.
7. Trims whitespace from activity names.
8. Sorts records chronologically.
9. Resets the DataFrame index.

This creates a consistent dataset for reliable downstream analysis.

---

## ✅ Input Validation

New activity entries are validated before being stored.

### Validation Rules

```text
Activity Type
    ↓
Must be one of the supported activities

Duration
    ↓
Must be greater than 0

Calories
    ↓
Must be greater than 0

Date
    ↓
Must be a valid date
```

Invalid input produces a clear error message instead of silently corrupting the dataset.

---

## 🔎 Filtering

The tracker supports flexible filtering by:

### Activity Type

```python
tracker.filter_activities(activity_type="Running")
```

### Date Range

```python
tracker.filter_activities(
    start_date="2026-09-01",
    end_date="2026-09-10"
)
```

### Custom Condition

The filtering method also accepts a callable condition for more advanced analysis.

---

## 🖥️ Interactive Dashboard

The notebook provides a menu-driven interface:

```text
=============================================
       PERSONAL FITNESS DASHBOARD
=============================================
1. Show all activities
2. Generate fitness report
3. Add new activity
4. Filter by activity
5. Show visual dashboard
6. Exit
```

This allows the project to function as an interactive application rather than only a collection of analysis cells.

---

## 🚀 Installation

### 1. Clone or download the project

Keep the notebook and CSV file in the same project directory.

### 2. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 3. Launch Jupyter

```bash
jupyter notebook
```

### 4. Open the notebook

```text
Personal_Fitness_Tracker_Dashboard.ipynb
```

### 5. Run the cells

Run the notebook from top to bottom and use the dashboard menu when prompted.

---

## 🧪 Testing & Edge Cases

The project includes checks for common invalid scenarios:

| Test Case | Expected Behavior |
|---|---|
| Empty activity type | Reject input |
| Unsupported activity | Reject input |
| Zero duration | Reject input |
| Negative duration | Reject input |
| Zero calories | Reject input |
| Negative calories | Reject input |
| Invalid date | Reject input |
| Empty dataset | Return safe zero metrics |

---

## 📅 Weekly Analysis

The notebook also performs time-based analysis using Pandas resampling to calculate:

- Weekly total duration
- Weekly total calories
- Weekly session count

This provides a foundation for identifying changes in activity volume over time.

---

## 💾 Data Persistence

When a new activity is successfully logged:

1. The record is added to the in-memory DataFrame.
2. Records are sorted by date.
3. The CSV file is updated.
4. The activity remains available after restarting the notebook.

---

## 🔐 Data & Privacy

The project uses a local CSV file and does not require an external database or cloud service.

No personal account, authentication system, or external fitness API is required by the current implementation.

---

## ⚠️ Limitations

- CSV storage is appropriate for a small educational project but is not designed for concurrent multi-user applications.
- Calorie values depend on the supplied dataset.
- The project does not include biometric measurements such as heart rate or VO₂ max.
- The current interface runs primarily through Jupyter Notebook.
- No authentication or user-profile management is implemented.

---

## 🔮 Future Enhancements

Potential upgrades include:

- 🎯 Personal fitness goals
- 📅 Monthly and yearly dashboards
- 📈 Progress and trend tracking
- 🗄️ SQLite/MySQL database support
- 🌐 Streamlit web dashboard
- 📱 Mobile-friendly interface
- 📤 PDF and Excel report export
- 🏆 Workout streaks and achievements
- 🔔 Goal reminders
- 👤 Multiple user profiles
- 🤖 Predictive fitness analytics
- 🔌 Integration with wearable/fitness APIs

---

## 🎓 Learning Outcomes

This project demonstrates practical experience with:

- Python programming
- Object-oriented programming
- Pandas
- NumPy
- Data cleaning
- Data validation
- Data aggregation
- GroupBy operations
- Date/time analysis
- Data filtering
- Matplotlib
- Seaborn
- CSV file handling
- Exception handling
- Interactive Python applications
- Basic testing and edge-case handling

---

## 👨‍💻 Project Files

vishvashkumar solanki
guidens bby Girish sir gondaliya

| File | Purpose |
|---|---|
| `Personal_Fitness_Tracker_Dashboard.ipynb` | Main application, analysis, tests, and dashboard |
| `fitness_activities.csv` | Fitness activity dataset |
| `README.md` | Project documentation |
| `charts/` | README visualization assets |

---

## 📄 License

This project is intended for educational and demonstration purposes.

If publishing it as an open-source project, consider adding an **MIT License** file.

---

<p align="center">
  <b>Personal Fitness Tracker Dashboard</b><br>
  Built with Python • Pandas • NumPy • Matplotlib • Seaborn • Jupyter
</p>
