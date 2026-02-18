
# Automotive Security System Data Cleaning

## Project Objective
This repository focuses on data cleaning and manipulation of vehicle immobilizer information using pandas. The main source is the spreadsheet `data/year_make_model_df.xlsx`, and the goal is to produce clean, manufacturer-specific datasets for further analysis or integration into applications.

## Input & Output Data
- **Input:** Raw spreadsheet (`data/year_make_model_df.xlsx`) containing vehicle, manufacturer, and security system data.
- **Output:** Cleaned `.csv` or `.xlsx` files for each manufacturer, stored in the `data/` folder.

## Main Operations with Pandas
Typical data cleaning steps include:
- Removing unnecessary columns: `df.drop(columns=[...])`
- Adding new columns based on logic: `df['new_col'] = ...`
- Filtering by manufacturer: `df[df['Make'] == 'Ford']`
- Handling missing values: `df.fillna('Default Value')`
- String cleaning and replacement: `df['col'].str.replace('old', 'new')`
- Exporting cleaned data: `df.to_csv('data/df_ford.csv', index=False)`

## Example Workflow
```python
import pandas as pd

# Load raw data
df = pd.read_excel('data/year_make_model_df.xlsx')

# Filter for a manufacturer
df_ford = df[df['Make'] == 'Ford']

# Remove unnecessary columns
df_ford = df_ford.drop(columns=['ParameterReset'])

# Fill missing values
df_ford['Security'].fillna('Information not available', inplace=True)

# Export cleaned data
df_ford.to_csv('data/df_ford.csv', index=False)
```

## Usage Instructions
1. Install dependencies:
	```bash
	pip install -r requirements.txt
	```
2. Open and run the desired notebook in Jupyter or VS Code to process and export cleaned data for each manufacturer.

## Directory Structure
```
security_system_data_cleaning/
├── data/                # Raw and cleaned data files
├── notesbooks/          # Jupyter notebooks for each manufacturer
├── requirements.txt     # Python dependencies
├── README.md            # Project documentation
```

## Dependencies
- pandas
- openpyxl

## Expected Results
- Cleaned, well-structured datasets for each manufacturer
- Consistent formatting and handling of missing values
- Ready-to-use files for further analysis or integration

## Notes
- All data cleaning is performed locally using pandas
- No external database is required; only spreadsheets are used
- Each notebook is tailored for a specific manufacturer due to differences in security systems

## License
MIT