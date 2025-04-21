# empirical_project
**Note** Please run all notebooks from the **root directory** of the project (where the 'data/' and 'notebooks/' folders are located) so that the relative paths work correctly.

This project investigates macroeconomic fragility by constructing a multi-dimensional profile of vulnerability across countries. It introduces the **Fragility Constellation**, a framework that visualises key economic weakness along key indicators such as debt, inflation, reserves, and external balances. The project is built in python and documented for full transparency and replicability.
## Project Structure
- data/: Raw and cleaned data files
- output/: Charts, graphs, and results
- notebooks/: Jupyter notebooks for scraping and analysis
## Requirements
This project requires the following Python libraries:
- pandas
- requests
- lxml
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