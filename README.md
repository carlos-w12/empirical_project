# empirical_project
This project investigates macroeconomic fragility by constructing a multi-dimensional profile of vulnerability across countries. It introduces the **Fragility Constellation**, a framework that visualises key economic weakness along key indicators such as debt, inflation, reserves, and external balances. The project is built in python and documented for full transparency and replicability.
## Project Structure
- scripts/: Python scripts for scraping and analysis
- data/: Raw and cleaned data files
- output/: Charts, graphs, and results
- notebooks/: Jupyter notebooks for workflow and analysis
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