# Crime Analysis in Los Angeles (2020–2023): A Data Analytics Case Study


**Author:** Andreza Eufrasio

**Stack:** Python, pandas, numpy, matplotlib

**Notebook:** analyzing_crime_los_angeles_case_study.ipynb


## Overview

This project analyzes reported crime incidents in Los Angeles between **January 1, 2020** and **July 3, 2023** using Python, pandas, and Seaborn. The goal is to identify actionable patterns in crime activity across **time**, **location**, **victim demographics**, and **weapon involvement**.

The notebook was originally developed from an educational DataCamp exercise and expanded into a full case study to demonstrate practical **data cleaning**, **feature engineering**, **exploratory data analysis**, **visualization**, and **insight generation** skills relevant to **Data Analyst** and **Data Scientist** roles.


## Business Context

Los Angeles is a large and diverse city with varying crime patterns across neighborhoods and time periods. Understanding when, where, and how crimes occur can help support more effective public safety strategies and resource allocation.

In this case study, the analysis is framed as a realistic public safety scenario, where insights could support organizations such as the Los Angeles Police Department (LAPD) or city planners.

The objective is to identify patterns that may inform decisions such as:

- prioritizing high-risk time windows
- identifying consistently elevated geographic areas
- understanding which victim groups are most affected
- distinguishing high-volume crimes from high-risk violent offenses


## Objectives

The analysis focuses on:

- identifying the most common crime types
- analyzing areas with the highest crime frequency
- examining temporal patterns (hour, weekday vs. weekend)
- exploring victim demographics
- assessing weapon involvement

## Dataset

- **File:** `data/crimes.csv`
- **Source:** DataCamp (educational version adapted from Los Angeles Open Data)
- **Unit of analysis:** Each row represents a single reported crime incident. This means that all analyses are conducted at the incident level rather than at the individual or location level.

### Key Variables
The dataset includes:

- crime date and time (`date_rptd`, `date_occ`, `time_occ`)
- location information (`area_name`, `location`)
- crime type (`crm_cd_desc`)
- victim demographics (`vict_age`, `vict_sex`, `vict_descent`)
- weapon and report information (`weapon_desc`, `status_desc`)

### Engineered Features
To support deeper analysis, the notebook creates additional variables such as:

- `year`
- `month`
- `month_name`
- `day_of_week`
- `hour`
- `minute`
- `time`
- `age_group`
- `weapon_used`
- `day_type`

## Key Questions Answered

1. Which hour has the highest frequency of crimes?
2. Which area has the highest frequency of night crimes?
3. How does crime distribution vary by victim age group?
4. What are the top 5 most common crime types?
5. How does crime distribution vary by victim gender?
6. Which area experiences the highest number of crimes during peak crime hours?
7. How do crime patterns differ between weekdays and weekends?
8. Which weekday has the highest crime frequency?
9. How does crime distribution vary by victim descent and gender?
10. How does weapon involvement vary across crime types?

## Methods & Tools

### Tools
- **Python**
- **pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **Jupyter Notebook**

### Analytical Methods

- data cleaning and standardization
- missing value detection and placeholder handling
- datetime conversion and time-based feature engineering
- categorical aggregation using `value_counts()`, `groupby()`, and `pivot`
- proportion analysis using `normalize=True`
- cross-tab and heatmap analysis
- validation through alternative methods in appendices

## Data Cleaning & Preparation Highlights

This project includes several cleaning and preprocessing steps designed to make the analysis robust and reproducible:

- Standardized column names to **lowercase snake_case**
- Preserved leading zeros in `TIME OCC` by reading it as string before conversion
- Converted date/time columns into usable datetime formats
- Created derived temporal features (`hour`, `day_of_week`, etc.)
- Grouped victim ages into interpretable age bands using `pd.cut()`
- Created a binary `weapon_used` indicator from `weapon_desc`
- Identified and replaced placeholder values such as `"?"`, `"N/A"`, and `"unknown"` with `NaN`
- Reviewed ambiguous categories (for example, low-frequency `"H"` in `vict_sex`) and excluded them where appropriate for clearer interpretation

## Key Findings

### 1) Crime peaks at midday

The highest crime frequency occurs at **12 PM**, suggesting that incidents rise with daytime activity and remain elevated through the afternoon.

### 2) Central is the most consistently high-risk area

The **Central** area has the highest frequency of **night crimes** and also records the highest number of crimes during **peak crime hours**, indicating a persistent concentration of crime risk.

### 3) Working-age adults are the most affected

Victims aged **26–34** represent the largest share of incidents, followed by the **35–44** group. The **0–17** group has the lowest number of crimes.

### 4) A few crime categories dominate the dataset

**Identity theft**, **battery**, **burglary**, **assault with a deadly weapon**, and **intimate partner-related offenses account** for a substantial share of reported incidents. 

This concentration suggests that a small number of crime categories drive a large portion of total incidents, indicating that targeted interventions in these areas could have a disproportionate impact on reducing overall crime.

### 5) Crime distribution by gender is broadly balanced
Male victims account for about **50%** of incidents and female victims about **48%**, indicating that crime in this dataset does not disproportionately affect one gender.

### 6) Peak-hour crime concentration is highest in Central

The **Central** area records the highest number of crimes during peak crime hours, reinforcing its position as a consistently high-crime location.

Other areas such as **77th Street** and **Pacific** also show elevated crime levels during peak hours, indicating that crime hotspots remain relatively stable throughout the day.

This suggests that peak crime periods amplify existing geographic patterns rather than shifting them, highlighting the need for targeted resource allocation in consistently high-risk areas.

### 7) Weekdays show substantially higher crime volume than weekends

Approximately **71.4%** of crimes occur on weekdays, compared with about **28.6%** on weekends. Among weekdays, **Friday** has the highest crime frequency.

### 8) Crime activity increases toward the end of the workweek

Among weekdays, **Friday** has the highest crime frequency, followed closely by **Thursday** and **Wednesday**, indicating a gradual increase in crime activity as the week progresses.

This pattern suggests that crime may be influenced by end-of-week behavioral and social dynamics, such as increased mobility and economic activity.

The relatively small differences across weekdays indicate that crime is consistently present throughout the week, but slightly intensifies toward the end of the workweek.

### 9) Multi-dimensional demographic disparities across victim descent and gender

Crime distribution varies across victim descent and gender, with certain demographic groups experiencing higher concentrations of incidents.

While both male and female victims are represented across all descent categories, some groups show noticeable imbalances, suggesting that crime exposure is not evenly distributed.

Analyzing these variables jointly reveals interaction patterns that would not be apparent when examining gender or descent independently, highlighting the importance of multi-dimensional analysis.

These differences should be interpreted cautiously, as they may reflect underlying population distribution, reporting practices, or socioeconomic factors rather than direct causal relationships.

### 10) Weapon involvement is strongly associated with crime severity

Most crimes in the dataset do **not** involve a weapon, indicating that a large portion of incidents are non-violent or involve lower levels of physical threat.

However, weapon involvement varies significantly by crime type. Violent offenses—such as assault with a deadly weapon and attempted homicide—show very high rates of weapon usage, while non-violent crimes such as identity theft, fraud, and document-related offenses show little to none.

This clear distinction highlights that weapon involvement is strongly linked to crime severity and can serve as an important indicator for differentiating between high-risk and lower-risk offenses.


## Why This Project Matters for Recruiters

This project is designed to demonstrate the practical skills expected in analytics roles:

### Technical Skills Demonstrated

- cleaning messy real-world style data
- working with missing values and ambiguous categories
- feature engineering from date/time data
- exploratory analysis with pandas
- grouping, pivoting, and summarizing categorical data
- building clear visualizations for decision support
- validating results through alternative methods

### Analytical Skills Demonstrated

- translating questions into structured analysis
- identifying trends across multiple dimensions
- connecting patterns to operational decision-making
- communicating findings clearly and cautiously
- distinguishing descriptive findings from interpretation and limitations

## Repository Structure

```text
.
├── analyzing_crime_los_angeles_final.ipynb   # final notebook
├── README.md                                 # project overview
└── data/
    └── crimes.csv                            # dataset
```

## How to Run the Notebook

1. Clone or download this repository.
2. Make sure the dataset file is placed at `data/crimes.csv` or update the notebook path if needed.
3. Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn notebook
```

4. Open Jupyter Notebook:

```bash
jupyter notebook
```

5. Run `analyzing_crime_los_angeles_final.ipynb` from top to bottom.

6. See answers under sections Q1–Q10, with insights and recommendations.

## Recommendations / Next Steps

Potential extensions of this analysis include:

- monthly or seasonal trend analysis
- hotspot analysis by area over time
- deeper crime-type segmentation by age, gender, or descent
- weapon involvement by area and time of day
- interactive dashboard development for monitoring crime trends
- predictive modeling for high-risk periods or locations

## Limitations

- This is an **educational version** of the original dataset.
- The analysis is based on **reported incidents**, which may not fully reflect actual crime occurrence.
- Some demographic comparisons may be affected by **population distribution** and **reporting behavior**.
- Variables such as `weapon_desc`, `vict_sex`, and `vict_descent` required data quality handling and should be interpreted carefully.

## Notebook

The final polished notebook is available here:

- [`analyzing_crime_los_angeles_final.ipynb`](sandbox:/mnt/data/analyzing_crime_los_angeles_final.ipynb)

## What This Project Demonstrates

This project showcases the ability to take a structured dataset and transform it into actionable insights through a complete analytical workflow.

It highlights:

- end-to-end exploratory data analysis  
- data cleaning and preprocessing using pandas  
- feature engineering from raw temporal and categorical data  
- structured problem-solving using real-world analytical questions  
- clear and professional communication of insights  
- validation of results using multiple approaches  
- ability to extend a guided exercise into an original, portfolio-ready case study

## Key Value

This project demonstrates how raw incident-level data can be transformed into meaningful insights that support data-driven decision-making in real-world scenarios.
