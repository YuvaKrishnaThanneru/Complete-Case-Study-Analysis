<div align="center">
  <h1 style="color:#8a2be2; margin-right: 20px;">Clipboard-Health Case Study Analysis 🔍</h1>
</div>

## 1. Introduction
This repository contains an analysis of the Payroll Based Journal (PBJ) Daily Nurse Staffing dataset, along with supporting datasets like the Quality Measures dataset and the State US Averages dataset. The primary goal is to identify potential staffing issues and provide actionable recommendations to improve healthcare staffing through various SQL queries. The results are visualized in Tableau dashboards for better interpretation.

## 2. Tools and Technologies
- **Python (Google Colab)**: For data pre-processing, cleaning, and formatting.
- **Amazon S3**: To store datasets and analysis outputs.
- **Amazon Athena**: For SQL querying and analysis.
- **Tableau**: For building interactive dashboards to visualize insights from the data.

## 3. Data Pre-processing
### Datasets:
- PBJ Daily Nurse Staffing, Quality Measures, and State US Averages datasets were collected.

### Data Cleaning:
- Duplicates and null values were handled using Python’s Pandas library.
- Date formats and staffing hour columns were reformatted for consistency across datasets.

### Uploading to S3:
- The cleaned datasets were uploaded to Amazon S3 for easier integration with Amazon Athena for SQL analysis.

## 4. SQL Queries and Analysis
Four key recommendations were generated based on the analysis:

### 4.1 Target Understaffed Facilities for Staffing Solutions
- **Objective**: Identify facilities with significant fluctuations in Registered Nurse (RN) or Certified Nursing Assistant (CNA) staffing hours.
- **Approach**:
  - SQL calculated daily staffing hours for RNs and CNAs.
  - Day-to-day variance in staffing hours was computed, followed by the calculation of standard deviations for each facility.
  - Facilities with an average census >50 and minimal census fluctuation were filtered, and those with high RN or CNA staffing fluctuations (>20) were flagged.
- **Recommendation**: Clipboard Health can target these facilities to provide flexible staffing solutions to stabilize the workforce.

### Result:
  <div align="center">
    <img src="https://github.com/user-attachments/assets/164b0519-2478-41d6-b779-6ab478117904" width="360" height="100">
  </div>

### 4.2 Promote Emergency Staffing Solutions During Peak Demand Periods
- **Objective**: Address the increased demand during weekends and holidays by offering emergency staffing.
- **Approach**:
  - Days were categorized as **Weekday**, **Weekend**, or **Holiday**.
  - SQL calculated the average administrative hours for RNs and Licensed Practical Nurses (LPNs) across these periods.
  - Facilities with significant administrative hour spikes during weekends/holidays (RN > 20 hours, LPN > 10 hours) were identified as candidates for emergency staffing.
- **Recommendation**: Clipboard Health can offer emergency staffing solutions to these facilities to avoid staff burnout and improve operational efficiency.

### Result:
  <div align="center">
    <img src="https://github.com/user-attachments/assets/6d58f342-2481-47dc-bc96-1280feb64b12" width="360" height="100">
  </div>

### 4.3 Enhance Healthcare Quality by Addressing Staffing Gaps
- **Objective**: Identify facilities with underperforming quality measures, low staffing hours, and reliance on contractor staffing.
- **Approach**:
  - SQL filtered facilities with underperforming metrics affecting long-stay residents based on the Five-Star Rating.
  - Facilities with zero direct RN, LPN, or CNA hours but some contractor reliance were flagged for staffing interventions.
  - Facilities were sorted by provider numbers for easy identification.
- **Recommendation**: Clipboard Health can focus on these facilities to provide direct staffing solutions to improve both quality of care and regulatory compliance.

### Result:
  <div align="center">
    <img src="https://github.com/user-attachments/assets/8ef8f0ce-4c32-450d-9bdd-5c4c2d6f139e" width="360" height="100">
  </div>

### 4.4 State Analysis - Contractor Dependency
- **Objective**: Identify states with high dependency on contractors to focus staffing solutions in those regions.
- **Approach**:
  - SQL aggregated contractor and employee staffing hours for RNs, LPNs, and CNAs across all states.
  - States were categorized based on contractor dependency into **Very High**, **High**, **Moderate**, or **Low** dependency levels.
  - These results were joined with state deficiency metrics to prioritize states needing staffing solutions.
- **Recommendation**: Target regions with high contractor dependency for marketing and sales to boost Clipboard Health staffing solutions.

### Result:
  <div align="center">
    <img src="https://github.com/user-attachments/assets/1235b034-00ab-4e06-8ef0-d32d04a9bd0d" width="360" height="100">
  </div>

## 5. Data Visualization with Tableau
- **Interactive Dashboards**: The results of the analysis were visualized using Tableau to create interactive dashboards. These provide a clear representation of staffing fluctuations, demand spikes, and facility-specific data to support decision-making.
- **Visuals**: The dashboards include detailed graphs that display RN/CNA fluctuations, state contractor dependency, and facility quality measures, helping identify key intervention points.

## 6. Conclusion
This repository documents a comprehensive analysis of nurse staffing data to provide actionable insights for Clipboard Health. By identifying facilities with staffing issues and analyzing state dependencies on contractors, the recommendations focus on improving healthcare quality and operational efficiency.
