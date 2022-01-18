# Greenhouse Gas (GHG) Regression Analysis

## Abstract
The goal of this regression analysis is to attempt to predict total greenhouse gas (GHG) emissions based on a facilities industry, unit and fuel types, parent company, and state of operation. Using linear regression techniques, I transformed the target variable – total GHG emissions – via a box-cox transformation and dropped financial feature variables that exhibited multicollinearity. The final model has an R2 of 0.482 (R2 adj = 0.479), with pulverized coal units having the largest effect on the total GHG. Other key features of higher GHG emissions facilities are combustion units, using coal or other fuel types, and being in the pulp/paper or metals/minerals industries. 

## Design
As the world works to combat climate change in an effort to contain the negative impacts of global warming, having a thorough understanding of the volume of emissions that companies put out is necessary to isolate industries that should be incentivized to transition to cleaner energy sources. The premise behind this analysis is to model green house gas emissions as a function of company size, industry, location, and other key features. With this we can determine the most likely large volume emitters based on a combination of industry, unit type, and fuel type. Ultimately, this analysis could benefit policy makers, company executives, and green energy lobbyists as they work to incentivize the switch to green energy across all industry sectors.

## Data
To tackle this problem I used the following datasets:
1. [Fuel_Unit Data](https://www.epa.gov/sites/default/files/2020-11/emissions_by_unit_and_fuel_type_c_d_aa_10_2020.zip)
> Dataset recording GHG emissions, fuel type, industry, unit type, etc. for facilities across the US. 
2. [Parent Company Data](https://www.epa.gov/sites/default/files/2020-11/ghgp_data_parent_company_10_2020.xls)
> Dataset linking facility ID to parent company
3. Webscraped Company Financial Data
> This data was scraped from wikipedia to track the financials of the largest parent companies (defined as number of facilities under their control) of GHG emitting facilities.
4. Webscraped State Electoral History
> Election data from 2000-2020 to get a sense of a states political lean as a proxy for the strength of their emission regulations. 


### The final dataset for modeling is as follows:

Target: 
> - `Total_GHG`

Features:
> - `Unit Type` (categorical - 9 subgroups)
> - `General Fuel Type` (categorical - 4 subgroups)
> - `Industry` (categorical - 9 subgroups)
> - `Unit Type` (numerical)
> - `Max Heat Capacity` (numerical)
> - `State%_Dem` (numerical)
> - `Revenue` (numerical)
> - `Operating Income` (numerical)
> - `Net Income` (numerical)
> - `Total Assets` (numerical)
> - `Total Equity` (numerical)
> - `# Employees` (numerical)

## Algorithms
**_Data Cleaning_**
1. Cleaning webscraped financial data in multiple currencies (Revenue, Operating Income, etc.)
2. Aggregating multiple years of election data to get state averages
3. Joining data on facility location with facility emissions (by facility ID), and merging the result with parent company financials 
4. Fill NaN values in financial data with grouped medians based on industry type

**_Feature Engineering_**
1. State average democratic lean based on election results as a proxy for regulation strength
2. Grouping like industries and unit types to limit categorical dummy variables
3. Log and Box-cox transformations on features and target

**_Regression Analysis_**
1. Linear Regression
2. Ridge Regression
3. Lasso Regression
4. Polynomial Regression

## Tools
- Pandas and numpy for managing and analyzing data
- Matplotlib and seaborn for plotting during regression analysis
- BeautifulSoup for webscraping
- Sklearn and statsmodels for regression analysis
