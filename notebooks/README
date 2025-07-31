# Vanguard A/B Test Analysis: Optimizing User Experience

## Table of Contents
1.  [Project Overview](#1-project-overview)
2.  [Project Goal & Hypotheses](#2-project-goal--hypotheses)
3.  [Key Performance Indicators (KPIs)](#3-key-performance-indicators-kpis)
4.  [Data Sources](#4-data-sources)
5.  [Project Structure](#5-project-structure)
6.  [Methodology](#6-methodology)
    * [Data Preprocessing](#data-preprocessing)
    * [KPI Calculation](#kpi-calculation)
    * [Statistical Analysis](#statistical-analysis)
    * [Visualization & Storytelling](#visualization--storytelling)
7.  [Results & Conclusion](#7-results--conclusion)
8.  [Recommendations](#8-recommendations)
9.  [Technical Stack](#9-technical-stack)
10. [How to Run/Reproduce](#10-how-to-runreproduce)
11. [Contact](#11-contact)

## 1. Project Overview

This project presents a comprehensive A/B test analysis conducted for Vanguard, evaluating the impact of a new user interface/process (Test group) against the existing design (Control group). The primary objective was to assess whether the new design leads to a more successful and efficient user journey, while identifying any potential negative trade-offs.

## 2. Project Goal & Hypotheses

**Goal:** To determine if the new design significantly improves the user experience as measured by key performance indicators, ultimately leading to a more effective process flow.

**Core Hypotheses:**
* **H0 (Null Hypothesis):** There is no statistically significant difference in key performance indicators (Completion Rate, Average Time Spent, Error Rate) between the new design (Test group) and the existing design (Control group).
* **H1 (Alternative Hypothesis):** There is a statistically significant difference in at least one of the key performance indicators between the new design (Test group) and the existing design (Control group).

## 3. Key Performance Indicators (KPIs)

The following metrics were tracked and analyzed:

* **Completion Rate:** The percentage of users who successfully complete the entire process.
* **Average Time Spent:** The average time users spend to complete the process.
* **Error Rate (Backward Movement):** The percentage of visits that involved users navigating backward in the process, indicating potential confusion or issues.

## 4. Data Sources

The analysis utilized two primary datasets, which were combined:

* `client_data.csv`: Contains demographic and account information for various clients.
* `process_data.csv`: Contains detailed logs of user interactions within the process, including steps, timestamps, and visit IDs.

The cleaned and merged data is saved as `df_full_ab_test_cleaned.csv` for subsequent analysis.

## 5. Project Structure

The project is organized into distinct phases, represented by Python notebooks and scripts:

vanguard-ab-test
├── data/
│   ├── raw/
│   │   ├── df_final_demo.csv
│   │   ├── df_final_experiment_clients.csv
│   │   ├── df_final_web_data_pt_1.csv
│   │   └── df_final_web_data_pt_2.csv
│   └── processed/
│       └── df_full_ab_test_cleaned.csv  # Output of data preprocessing
├── notebooks/
│   ├── 01_data_ingestion_cleaning.ipynb   # Initial data loading, cleaning, and merging
│   ├── 02_kpi_calculation_analysis.ipynb  # KPI derivation and exploratory data analysis
├   ├── 03_hypothesis_testing_evaluation.ipynb # Statistical hypothesis testing and final 
├   ├── 04_04_further_analysis_segmentation.ipynb
│
├── tableau/                  # Folder containing Tableau workbook/story
│   └── Vanguard_AB_Test_Dashboard.twbx  # Packaged Tableau Workbook
├── README.md                            # Project README file (this file)


## 6. Methodology

### Data Preprocessing
The `01_data_ingestion_cleaning.ipynb` notebook handles the initial data preparation:
* Loading raw client and process data.
* Cleaning data inconsistencies (e.g., handling missing values, standardizing formats).
* Merging the two datasets on relevant keys (`client_id`).
* Ensuring data types are appropriate for analysis.

### KPI Calculation
The `02_kpi_calculation_analysis.ipynb` notebook focuses on deriving the key performance indicators:
* Defining what constitutes a "completed process" based on sequential steps.
* Calculating `Time Spent` for each visit.
* Identifying `Backward Movement` within the process flow to quantify error rates.
* Performing initial exploratory analysis and visualization of KPIs.

### Statistical Analysis
The `03_hypothesis_testing_evaluation.py` script performs the rigorous statistical evaluation:
* **Data Aggregation:** Data is aggregated to the visit level to ensure independent observations for statistical tests.
* **Significance Level:** An alpha ($\alpha$) of 0.05 (5%) is used for all tests.
* **Completion Rate (Proportion Z-test):** Compares the proportion of completed visits between Test and Control groups.
* **Average Time Spent (Independent Samples T-test):** Compares the mean time spent for *completed* visits between the two groups. Levene's test is used to assess equality of variances, determining whether to use Student's or Welch's t-test.
* **Error Rate (Proportion Z-test):** Compares the proportion of visits with backward movement between Test and Control groups.
* **Confidence Intervals:** Confidence intervals are calculated for differences in proportions to provide a range of plausible effect sizes.

### Visualization & Storytelling
* Python (Matplotlib, Seaborn) is used within the notebooks for exploratory data visualization.
* **Tableau Dashboards** are created for interactive and executive-level presentation of results, providing a guided story through the findings. This includes:
    * Executive Summary Dashboard
    * Detailed Demographic Insights Dashboard
    * Participant Demographics Dashboard
    * A Tableau Story for the overall conclusion and recommendations.

## 7. Results & Conclusion

**Overall A/B Test Conclusion:**

The new design (Test group) significantly improved the **Completion Rate** (by +8.69% with P-value < 0.0001), indicating a more successful user journey.

However, this came with statistically significant negative impacts:

* **Average Time Spent** was higher for the Test group (P-value = 0.0193), suggesting the new process is slightly slower.
* **Error Rate (Backward Movement)** was also significantly higher (P-value < 0.0001), indicating potential confusion or navigation issues within the new design.

## 8. Recommendations

1.  **Investigate Root Causes:** Conduct UX research (e.g., user testing, heatmaps, session recordings) to pinpoint *why* time spent and error rates increased despite higher completion.
2.  **Iterative Refinement:** Consider a phased rollout or A/B testing specific components of the new design to mitigate negative impacts while preserving the increased completion rate.
3.  **Quantify Trade-offs:** Further analyze the business impact of a higher completion rate versus increased time/errors (e.g., does the higher completion rate outweigh the negative user experience points?).

## 9. Technical Stack

* **Programming Language:** Python
* **Data Manipulation:** `pandas`, `numpy`
* **Statistical Testing:** `scipy.stats`, `statsmodels.stats.proportion`
* **Data Visualization:** `matplotlib`, `seaborn`, Tableau

## 10. How to Run/Reproduce

1.  **Clone the repository:**
    ```bash
    git clone <repository_url>
    cd <repository_name>
    ```
2.  **Set up Python Environment:**
    ```bash
    # Using pip
    pip install -r requirements.txt
    # Or using conda
    # conda create -n vanguard_ab_test python=3.9
    # conda activate vanguard_ab_test
    # conda install pandas numpy matplotlib seaborn scipy statsmodels
    ```
3.  **Place Raw Data:** Ensure `client_data.csv` and `process_data.csv` are placed in the `data/raw/` directory.
4.  **Run Notebooks Sequentially:**
    * Open and run `01_data_ingestion_cleaning.ipynb` to process and clean the data. This will generate `df_full_ab_test_cleaned.csv` in `data/processed/`.
    * Open and run `02_kpi_calculation_analysis.ipynb` for KPI derivation and initial visualizations.
5.  **Run Hypothesis Testing Script:**
    ```bash
    python scripts/03_hypothesis_testing_evaluation.py
    ```
    The script will print the statistical test results and final recommendations to the console.
6.  **Explore Tableau Dashboards:** Open the `Vanguard_AB_Test_Dashboard.twbx` file in Tableau Desktop to interact with the dashboards and story.

## 11. Contact

For any questions or further information, please contact:
[Mahmoud Gobran/ Pedro Gonçalves/Doarsa Tushi]

---