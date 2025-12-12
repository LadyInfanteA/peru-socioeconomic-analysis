# Socioeconomic analysis in Peru

README: Proximity to Wealth Analysis - Data Documentation Project Overview
Research Question: "Does living near wealth help or hurt the poor? A spatial analysis of service quality, economic behavior, and social networks across neighborhood boundaries in urban Peru."
Course: Exploratory Data Analysis and Visualization (EDAV)
Dataset: ENAHO 2025 (Encuesta Nacional de Hogares - Peru National Household Survey)
Geographic Focus: Urban Lima, Peru

Data Acquisition
Source
URL: INEI - Instituto Nacional de Estadística e Informática
Survey: ENAHO 2025 (Encuesta Nacional de Hogares)
Format: Multiple CSV files extracted from survey modules
Access Date: 2025
Data Collection Method

Web scraping from INEI public microdata portal
Downloaded modular survey files covering household characteristics, social programs, infrastructure, and services
Census-based household survey with multi-stage sampling

Raw Data Tables
Total Variables Extracted: 1,988 raw variables
Tables Used in Analysis: 8 modules
Final Sample Size: 1,355 households

Data Cleaning Process
1. Missing Data Handling
Rule 1: Column Retention Threshold
python# Keep only columns with ≥50% non-missing values
keep_cols = df.columns[df.notna().sum() / len(df) >= 0.5]
Rule 2: Spanish Text Standardization
python# Replace Spanish missing indicators with NA
missing_indicators = ['pass', 'paso', 'PASS', 'PASO', 'no sabe', 'no aplica']
df.replace(missing_indicators, np.nan, inplace=True)
Rule 3: Numeric Missing Codes
python# INEI uses specific codes for missing data:
# 99 = "Does not know"
# 999 = "Does not apply"  
# 9999 = "No response"
# 99999 = "Not applicable"
# 999999 = "Refused to answer"

# Replace with NA for analysis
missing_codes = [99, 999, 9999, 99999, 999999, 9.9]
df.replace(missing_codes, np.nan, inplace=True)
Result:

Original: 1,988 variables
After filtering: 763 variables retained
Missing data patterns documented in analisis-2.json


2. Variable Translation
Process:

All Spanish column names translated to English
Preserved original Spanish in value labels for cultural context
Created bilingual data dictionary
