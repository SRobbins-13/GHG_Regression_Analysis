# Exploratory Data Analysis Project Proposal
#### Samuel Robbins

### Premise/Question:
As the world works to combat climate change in an effort to contain the negative impacts of global warming, having a thorough understanding of the volume of emissions that companies put out is necessary to isolate industries that should be incentivized to transition to cleaner energy sources. The premise behind this analysis is to model green house gas emissions as a function of company size, industry, location, and other key features. With this we can determine the most likely large volume emitters based on a combination of industry, unit type, and fuel type. Ultimately, this analysis could benefit policy makers, company executives, and green energy lobbyists as they work to incentivize the switch to green energy across all industry sectors.

### Data Description:
- The primary data set will be green house gas (GHG) data from the [EPA](https://www.epa.gov/ghgreporting/ghg-reporting-program-data-sets).
> A single row of data will represent GHG emitting units at different facilities (e.g. Facility name, parent company, state, industry type, unit name/type, fuel type, methane emissions, and nitrous oxide emissions)
- The secondary data set will contain important company demographic and financial data. This will be scraped from wikipedia, company websites, or news sites.
> A single row of data will represent demographic and financial information for the parent companies of the GHG emitters (e.g. # of employees/offices, revenue, operating income, etc.)
- The target for this regression analysis will be the total GHG emissions (Methane and Nitrous Oxide) produced by a company.

### Tools:
- I will use BeautifulSoup, Selenium, ChromeDriver to web scrape company demographic, financial data, and other data
- I will use pandas, numpy, matplotlib/seaborn for exploratory data analysis on the GHG and company data
- I will use statsmodels and sklearn for regression analysis

### Minimum Viable Product:
A Minimum Viable Product for this project is  a regression that predicts GHG emissions primarily by industry and company size.
