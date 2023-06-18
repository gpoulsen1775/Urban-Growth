<h1> Affects of Migration on Housing Affordability </h1>

<a>For TLDR, here is the URL to End Result: https://public.tableau.com/app/profile/gp5012/viz/CountyHPI/Dashboard1 </a>

<u> <h2> Preface </h2> </u>

<p> Growing up in St.George, Utah, one of the fastest growing regions in the United States over the last 25 years, always made me wonder at the wisdom of a city who's primary intention was to grow subject only to the bounds of consumer wants. 

Buyers want more space to themselves? Room is made where the farmer used to grow their crops. Buyers don't want to live in the middle of town? New subdivisions are planned just beyond last year's new subdivisions. Buyers want a better view? The city redraws the zonings for public land so that houses can be built on top of the bluff. Buyers become residents. More residents lead to more tax revenue, more business owners, more jobs, etc. People are often well off. 

Years go by, the process continues on again and again and again. The farmer's field is now a well established subdivision, not unlike the subdivisions that buyers had originally moved from. The new subdivision on the edge of town becomes the old subdivision. That nice view that you moved to town for is now private property reserved for the enjoyment of a select few citizens. Buyers see that the town is the same place they're moving to get away from. Residents of the now city grow tired of the traffic, the oversized buildings, the impersonable nature of a city, and they begin moving else where. Years go by, the process continues on again and again and again. 

We've seen the benefits of the growth. Jobs have come to our now city. People are well off. Some residents grow tired of the now city. Some residents become buyers elsewhere. Still, the city's growth has not yet touched the fence of consumer want that lays somewhere in the far off distance. People still move. Growth will be inevitable for many years to come. 

Personally partaking in this observed growth cycle has left me to think on ways we can better understand the affects of unfettered growth on everyday people. My reflections brought me to this hobby project wherein I consider the affects of growth (specifically attributable to migration) on housing affordability and pricing, a relevant consideration for residents of any region. 

 </p>

<u> <h2> The Project </h2> </u>

This project is structured under the process model of extract, clean, wrangle, and analyze. Extraction, cleaning, and wrangling was done in Python through Pandas. Analysis was done using Tableau. Data was extracted from the following sources:

<h3> <a href="https://www.fhfa.gov/DataTools/Downloads/Pages/House-Price-Index-Datasets.aspx">HPI Index</a> </h3>

House price indexes were pulled from apprxoimately 400 distinct regions over multiple years ranging from 1986 onward. The baselines for the index are set from regional averages from the year 1995. Data was conviniently stored in a csv for users. 

<h3> <a href="https://simplemaps.com/data/us-cities">US Cities to County Fips</a> </h3>

This file was pulled from a website relating U.S. cities to county fip codes. The relation allows us to join our HPI Index to our migration data. Data was conviniently stored in a csv for users. 

<h3> <a href="https://www.irs.gov/statistics/soi-tax-stats-migration-data">IRS Migration Data</a> </h3>

This data was put together by the IRS. It gives counts of migrants from one city to another and it is based on tax filings. 

Datasets were combined in order to provide a table that includes the following fields:

<b> county: </b> A numeric identifier for county.

<b> state: </b> A numeric identifier for state. 

<b> county_fips: </b> A numeric identifier uniquely identifying each count. This is treated a the primary key. 

<b> year: </b> Years

<b> net_migration: </b> A count of net migrants for each county and year.

<b> pop: </b> The county population evaluated at each year. 

<b> net_migration_percentage: </b> net_migration divided by the population

<b> index_nsa: </b> A non-seasonally adjusted housing price index with a regional baseline on the year 1995. 

All fields had needed data except for the population data; Some years were missing population data, so annual federal growth rates and net migration was used to impute missing years as a best estimate. Used federal growth rates were taken from the following <a href='https://www.macrotrends.net/countries/USA/united-states/population-growth-rate '> website. </a>

The final table includes longitudinal data from 2005 to 2019. 

<u> <h2> The Analysis </h2> </u>

Finally, a cohort analysis was performed using Tableau. The user is given the freedom to pick the cohort of counties based on what percentile they rank in for average migration rate over the 15 year time span. For instance, the user could choose to see how the top quartile of counties in average migration rate compare to the bottom quartile of counties in average migration rate with reagards to each cohort's housing affordability. The dashboard displays the longitudinal trajectory of the mean and variance for each cohort. It also displays a ridge plot detailing each cohorts distributions by year. The dahsboard can be found <a href= "https://public.tableau.com/app/profile/gp5012/viz/CountyHPI/Dashboard1">here. </a>

Two observable results regarding counties were demonstrated. Counties experiencing high migration have less affordable housing and more reliable housing prices. By 2019, the high migration cohort had a housing price index 25 percentage points higher than the control group. Consequently, one down side to promoting growth based on high migration rates is that housing becomes less affordable. This makes intuitive sense given that high migration rates increase market demand. 

<u> <h2> Some Notes </h2> </u>

One portion of this project that I would like to build out further is the application of inferential statistics. I would like to apply a series of year wise, permutation tests that determine whether or not the data from each cohort come from the same underlying distribution. I believe I would need to make a correction to these tests to keep the type 1 error rate under .05 for the entire series of hypothesis tests. Unfortunately, I do not have enough time to build this out yet, so I will likely return to this portion of the project down the line. 
