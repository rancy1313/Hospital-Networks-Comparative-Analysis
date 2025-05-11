# Hospital-Networks-Comparative-Analysis
PostgreSQL ETL pipeline and interactive Tableau dashboard comparing hospital networks' readmission rates, analyzing factors affecting patient outcomes using MIMIC-IV and Medical Clean datasets

## Project Overview
This project delivers a comprehensive comparative analysis between two hospital networks: Medical Clean and Beth Israel Deaconess Medical Center (BIMC). Using PostgreSQL for ETL processes and Tableau for visualization, the analysis evaluates hospital performance through readmission rates and hospitalization durations to identify operational strengths and improvement opportunities.

## [View Interactive Dashboard on Tableau Public](https://public.tableau.com/app/profile/rancel.hernandez7504/viz/D211_assessment/D211Presentation?publish=yes)

> **Note:** The original project utilized a PostgreSQL database connection as part of the academic assignment requirements. For GitHub portfolio purposes, the Tableau workbook has been modified to connect to CSV data files, making it portable while maintaining identical visualizations and findings.

> **Note on Dashboard Formatting:** The dashboard layout on Tableau Public may appear slightly compressed compared to the original design. 

## Key Findings
- **Hospitalization Duration Disparity**: BIMC demonstrated significantly shorter hospital stays (6 days for readmitted patients) compared to Medical Clean's concerning 64 days average
- **Readmission Rate Comparison**: BIMC's overall readmission rate (20.68%) was lower than Medical Clean's (36.64%)
- **Care Consistency**: Medical Clean showed consistent care delivery with stable readmission rates across conditions (~37%), while BIMC exhibited greater variation (23.35% to 57.86%)
- **Gender Patterns**: Males consistently experienced higher readmission rates than females in Medical Clean, while BIMC showed condition-dependent gender variations
- **Age Correlation**: Both networks showed increasing readmission rates with patient age, with BIMC achieving notably lower rates (13.96%) for younger patients (18-39)

## Technical Implementation
### ETL Process
1. **Database Structure Setup**: Created and populated three related tables (mimic_patients, mimic_admissions, drg_codes) with appropriate primary/foreign key relationships
2. **Readmission Status Calculation**: Added readmission_status column using 30-day criteria, calculating time between visits and flagging readmissions
3. **Initial Hospitalization Calculation**: Developed metrics for comparing initial hospital stays, with separate methodologies for readmitted vs non-readmitted patients
4. **Condition Mapping**: Created patient_conditions table using pattern matching to align MIMIC-IV descriptions with Medical Clean condition categories
5. **Data Standardization**: Normalized gender values, created consistent age ranges, corrected column names, and removed negative interval anomalies
6. **Dataset Integration**: Combined datasets through unions and joins, assigned network identifiers, and unpivoted health conditions for unified analysis

### Tableau Dashboard
The interactive dashboard features four main visualizations designed to provide stakeholders with actionable insights:
- **Scatter Plot**: Compares hospital durations across networks by health condition and readmission status
- **KPI Table**: Displays patient distribution by gender and health status across networks
- **Pie Charts**: Shows overall readmission rates for each network with percentage breakdowns
- **Heat Map**: Identifies patient population density by age group and health condition

## Navigating the Dashboard

### Initial Access
1. Navigate to the story named "D211 Presentation" in the [Tableau Public dashboard](https://public.tableau.com/app/profile/rancel.hernandez7504/viz/D211_assessment/D211Presentation?publish=yes)
2. Start with the Introduction page to view creator information and assignment name

### Dataset Information
1. Click on the "Datasets" tab at the top
2. Review Medical Clean dataset information (left side)
3. Review MIMIC IV dataset information (right side)

### Main Dashboard Navigation
Click on the "Comparative Analysis" tab to access the interactive dashboard featuring all visualizations.

### Key Visualizations
* **Scatter Plot (Top Left)**: Illustrates hospital duration patterns across networks by displaying the average admission duration for each health condition. Different shapes represent networks, while colors distinguish between readmitted and non-readmitted patients.
* **KPI Table (Top Right)**: Provides a breakdown of patient counts by gender and health condition, segmented by network and readmission status. Includes row totals to show population totals by readmission status.
* **Pie Charts (Bottom Left)**: Display readmission rates for each network, comparing percentages of readmitted and non-readmitted patients, with average stay durations available in tooltips.
* **Heatmap (Bottom Right)**: Visualizes patient population density by age group and health condition, using color intensity to highlight concentrations.

### Filter Guide
Available filters to customize your view:
* **Filter Conditions:** Adjusts the available condition options to show the top or bottom 5 health conditions based on the percentage of readmitted patients with each condition.
* **Network:** Filters visualizations by the two networks being compared.
* **Health Status:** Distinguishes whether patients had a specific condition.
* **Readmission Status:** Filters by readmission within 30 days of initial hospitalization.
* **Age Groups:** Filter by age ranges (18-39, 40-59, 60-91).
* **Gender:** Filter by Female or Male.
* Each graph can also act as an interactive filter.

### Tips
* Use multiple filters simultaneously for a detailed analysis
* Hover over elements to view additional details in the tooltips
* There is a filter guide located in the top right corner of the dashboard, above the filters
* Some visualizations have restricted filter options to maintain comparison capabilities

## Data Limitations & Methodology Considerations
The analysis addressed three key data interpretation challenges:

1. **Health Condition Persistence**: Assumed that conditions remained active throughout a patient's history with BIMC, as most are chronic conditions unlikely to resolve after single hospitalizations.

2. **Readmission Rate Calculation**: Aggregated MIMIC-IV's multiple admission records to patient level to enable direct comparison with Medical Clean's single-admission approach.

3. **Initial Days Calculation**: Used a visit-centric approach for MIMIC-IV data, calculating separate averages for readmitted and non-readmitted patients to maintain focus on admissions leading to readmissions.

## Recommendations
1. **Protocol Implementation**: Explore and implement BIMC protocols to reduce Medical Clean's hospital stay durations
2. **Targeted Interventions**: Develop strategies for male patients who show consistently higher readmission rates
3. **Preventive Care Programs**: Enhance preventive care for older patients with conditions common in this demographic
4. **Standardized Approach**: Maintain the current standardized approach to care while focusing on reducing overall readmission rates

## Technologies Used
- **PostgreSQL**: Database management and ETL operations
- **PGAdmin**: Database administration tool for data processing
- **Tableau**: Data visualization and interactive dashboard development

## Files in this Repository
- `data_prep.sql`: Complete ETL process for transforming and integrating the datasets
- `D211_Analysis_Report.pdf`: Comprehensive analysis document with detailed findings
- `D211_Dashboard.twbx`: Tableau workbook for local exploration (requires Tableau Reader or Desktop)

## Future Work
Future analyses would benefit from standardized data collection methods to enable more direct performance comparisons and uncover additional opportunities for enhancing patient care.

*This project was completed as part of the Advanced Data Acquisition course (D211) at Western Governors University.*
