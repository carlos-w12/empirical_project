# empirical_project
**Note** Please run all notebooks from the **/notebooks/** folder so that the relative paths to **/data/** work correctly.

This project investigates macroeconomic fragility by constructing a multi-dimensional profile of vulnerability across countries. It introduces the **Fragility Constellation**, a framework that visualises key economic weaknesses along key indicators such as debt, inflation, reserves, and external balances. The project is built in Python and documented for full transparency, reproducibility, and open analysis.
## Project Structure
- data/: Empty by default. Used by the code for saving scraped data.
- data_backup/: Contains all backup CSV files produced during the project, including both scraped datasets and final outputs. 
- notebooks/: Jupyter notebooks for scraping and analysis.
## Requirements
This project requires the following Python libraries:
- pandas
- requests
- lxml
- scikit-learn
- statsmodels
- plotly
- matplotlib
## Project Documentation
### Step 1 - Scraping the data
- Scraped macroeconomic indicators from the World Bank API (2010-2022) using Python's 'requests' and 'pandas' libraries
- Indicators and their respective World Bank indicator codes:
    - **Central government debt, total (% of GDP)** - GC.DOD.TOTL.GD.ZS
    - **Inflation, consumer prices (annual %)** - FP.CPI.TOTL.ZG
    - **Total reserves in months of imports** - FI.RES.TOTL.MO
    - **Current account balance (% of GDP)** - BN.CAB.XOKA.GD.ZS
    - **Foreign direct investment, net inflows (% of GDP)** - BX.KLT.DINV.WD.GD.ZS
    - **GDP growth (annual %)** - NY.GDP.MKTP.KD.ZG
- Scraped list of countries and territories by the United Nations geoscheme to build custom regional aggregates
### Step 2 - Cleaning and merging the data
- Aggregates were removed due to inconsistency across indicators (some appear only under certain variables or are composed differently)
- Country-level data was isolated by identifying the position of known countries and slicing the dataset accordingly
- Used a dictionary to align country names for World Bank data with United Nations geoscheme namings
- Merged all six indicators on 'country', 'iso', and 'year', using an inner join to ensure full data availability
- Merged the cleaned data with UN region classifications to allow for aggregates to be analysed
### Step 3 - Regression Modelling and Fragility Score Construction
- Standardised all macroeconomic indicators using z-score normalisation 
- Applied OLS regression to estimate the relationship between current-year macroeconomic conditions and next-year GDP growth
- Extracted regression coefficients as weights for each indicator, representing their relative importance in predicting fragility
- Constructed a **Fragility Score** for each country-year as the weighted sum of indicators, where higher scores represent higher fragility
- Applied standard min-max normalisation to the Fragility Scores to rescale them between 0 and 1, making country comparisons interpretable
- Saved the final dataset, including raw Fragility Scores and normalised versions, into 'fragility_scores.csv'
### Step 4 - Data Visualisation
- Built animated bar charts to show the evolution of average regional Fragility Scores between 2010 and 2021
- Used robust min-max normalisation (10th-90th percentile) for individual indicators to create consistent radar profiles across countries and years
- Constructed animated radar charts to visualise multi-dimensional fragility profiles for each country over time
- Developed an interactive line plot allowing users to explore Fragility Scores for individual countries, toggling between standard min-max and robust min-max normalisation methods. Standard min-max is intended to highlight fringe cases, while robust min-max is more appropriate for analysing 'typical' countries
- Highlighted Zambia with a dedicated radar chart and Fragility Score evolution plot to demonstrate structural shifts in economic vulnerabilities