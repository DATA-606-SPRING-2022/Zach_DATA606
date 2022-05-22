# DATA 606 Capstone Project

# Predicting Maryland Home Prices and Finding their Value


Recorded Presentation: [Recorded Presentation](https://youtu.be/M-Pc2erqVoM)


### Background Information

This project is to create a model on predicting home prices in Maryland, more specifically in Anne Arundel, Harford, Baltimore, and Howard counties.  In today's very competitive market, it is difficult for first time home buyers like myself to jump into.  Prices are high and so are desires for a home, so a model in finding homes that are undervalued or offer the most based on a buyer's preferences gives the buyer confidence that they are getting the best house for their money.  With that, they can better know what they want, at what price it will take to get what they want, and be able to make an offer quickly and confidently when their dream home is on the market.  Buying a home is one of the biggest purchases people make in their life, and thus making the correct decision is important and comforting.  Investors should also be interested in this model as it relates to finding value in certain properties that are good for positive cash flow based on its features.

Many benefits come out of the exploratory data analysis as well as the final model.  Seeing the price differential between homes in certain areas, certain styles, and with different features gives a better understanding of where exactly the value in a home comes from and what areas, styles, and features are most costly.  Home buyers, in their heads, place different values on different features of a home and need to understand what that means in terms of their budget.  For example if the buyer really wants to live waterfront, how much does that cost vs a new construction home not on the water and with 1,000 more square feet than the waterfront home would have?  From that the buyer can better determine if they think the cost of living on the water is worth it in comparison to a nicer home not on the water for the same budget.  The project also uncovers things like whether or not waterfront homes appreciate faster, and maybe that helps them feel more comfortable with the purchase of the waterfront home if decided that the buyer values that more.  All in all, uncovering facts like this and being able to weigh the different features of a house more effectively is important to prospective home buyers and investors.

### About the Data

The data used here comes straight from a dump of a local Real Estate Agent from the MLS (Multiple Listing Service) software.  The max the real estate agent could dump was 5,000 rows per file, so I have 20 total files, containing a cumulative 90,758 homes of which were sold in the counties of Anne Arundel, Harford, Baltimore and Howard over the last 5 years.  The data contains fields such as:
  - category
  - list date
  - off market date
  - settlement date
  - original price
  - list price
  - sold price
  - address 
    * city
    * state
    * zip
    * county
  - school district
  - acres total
  - whether its a house for older persons
  - condo association
  - homeowners association
  - age
  - square footage
  - style
  - number of floors
  - whether it has a basement
  - garage spaces
  - fireplace
  - waterfront
  - whether it is new construction
  - number of bedrooms
  - number of bathrooms

Among other attributes as well.  It is credible as it is straight from the Real Estate Agent, relatively clean / consistent but does have some missing values.

Data here: [Raw Data](https://github.com/zvance1/Zach_DATA606/tree/main/RawData)

Cleaned Data: [Cleaned Data Sets](https://github.com/zvance1/Zach_DATA606/tree/main/CleanedData)

The unit of analysis is individual homes.  Again, targeting Anne Arundel, Harford, Baltimore, and Howard counties for historical anlysis and future predictions.

### Questions to be Answered

Key question to answer:
  - What impacts the price the most?  With a ranking of features that have the largest impact on price.

Exploratory Questions:
  - What is the best month to buy a house in?
  - Have home prices gone up faster in certain areas over others?
  - How much do waterfront homes cost in comparison to non-waterfront?
  - Has the number of acres for new construction homes gone down over time?
  - How much does new construction cost in comparison to non new construction?
  - Is there more new construction in certain areas?
  - Did homes tend to go more above or below listing price during any specific time period?
  
### EDA Analysis

In the EDA analysis pyspark is used to query the data in order to answer the desired questions.

Begining with the question of whether or not home prices have gone up faster in certain areas over others:

![PricePerCountyPerMonth](https://github.com/zvance1/Zach_DATA606/blob/main/Images/PricePerCountyPerMonth.png?raw=true)

From the above chart we can easily see that Howard county is the most expensive, followed by Anne Arundel, then by both Harford and Baltimore being similar price levels.  Interestingly, the price movements up and down seem to follow the same trend over the course of the year.  As the price in Howard goes up towards the summer months, so does the price in Anne Arundel and the other counties, at about the same rate as well.  Based on this visualization it seems that prices for houses are the lowest in February and March of each year.

![PricePerCountyPerYear](https://github.com/zvance1/Zach_DATA606/blob/main/Images/PricePerCountyPerYear.png?raw=true)

From the above chart we can easily see the upward trend in the cost of house prices over the years.  We see again the same ordering of price levels of the 4 counties and increases at similar rates.  Home prices look to have peaked in 2021 and have so far leveled off or decreased slightly so far into 2022.

![medianPricePerWaterfrontAnneArundel](https://github.com/zvance1/Zach_DATA606/blob/main/Images/medianPricePerWaterfrontAnneArundel.png?raw=true)

![medianPricePerWaterfrontBaltimore](https://github.com/zvance1/Zach_DATA606/blob/main/Images/medianPricePerWaterfrontBaltimore.png?raw=true)

![medianPricePerWaterfrontHarford](https://github.com/zvance1/Zach_DATA606/blob/main/Images/medianPricePerWaterfrontHarford.png?raw=true)

![medianPricePerWaterfrontHoward](https://github.com/zvance1/Zach_DATA606/blob/main/Images/medianPricePerWaterfrontHoward.png?raw=true)

Looking at the above chart, it is clear that Anne Arundel County waterfront homes look to have increased pretty dramatically from 2019 to 2021.  When looking at 2022, I would engourage to see it as valuable information but at the same time not to the same extent as the other years as there is not as much data for it only two months into the year (Howard hasn't had any waterfront home sales yet this year).  In Anne Arundel county, the price difference between the medians of waterfront and non waterfront is also pretty significant with the median for non waterfront being down around 400k and waterfront up over 1 million.  The cheapest is non waterfront in Baltimore county, and the difference between waterfront and non waterfront in Baltimore county is not as significant.  Waterfront is consistently more expensive than non waterfront in all of the counties, but to different degrees.

![medianAcresPerNewConstructionPerCounty](https://github.com/zvance1/Zach_DATA606/blob/main/Images/medianAcresPerNewConstructionPerCounty.png?raw=true)

In the above chart we see that there has been a slight downward trend in the size of new construction lots, more steadily for Anne Arundel and Baltimore counties.  The median in those counties has stayed in the 0.2 acre range, and that is already really small so it makes sense that the downward trend has only been slight - it is tough to get much smaller than that.  Interestingly, Howard, which we saw as the most expensive, and Harford, which we saw as the least expensive alongside Baltimore County look to have their new construction lot sizes be slightly larger, and the downward trend is not as clear or evident for those counties.  Howard and Harford counties have more land, so it will be interesting to see where the price difference between the two comes from whether it be mainly rooted in location or if homes in Howard tend to be larger than that of Harford.  For Howard, in 2022, there have only been 5 new construction home sales, 3 of which were 1 acre lots, the other 2 being 0.14 and 0.24 acres, so I'd expect that as we get further into 2022 that number come down.  Harford and Howard also have a lesser volume of homes than Anne Arundel and Baltimore counties, making their numbers less consistent.

![medianPricePerNewConstructionAnneArundel](https://github.com/zvance1/Zach_DATA606/blob/main/Images/medianPricePerNewConstructionAnneArundel.png?raw=true)

![medianPricePerNewConstructionBaltimore](https://github.com/zvance1/Zach_DATA606/blob/main/Images/medianPricePerNewConstructionBaltimore.png?raw=true)

![medianPricePerNewConstructionHarford](https://github.com/zvance1/Zach_DATA606/blob/main/Images/medianPricePerNewConstructionHarford.png?raw=true)

![medianPricePerNewConstructionHoward](https://github.com/zvance1/Zach_DATA606/blob/main/Images/medianPricePerNewConstructionHoward.png?raw=true)

Here we see that new construction is consistently more expensive than non new construction in each and every county, to different degrees in each county.  Again Baltimore, non new construction shows as the cheapest option and we see Howard new construction as the most expensive option.  This is consistent with the overall average prices we saw per county earlier in the analysis and the same general increase in prices across the board.

![countOfNewConstructionPerCounty](https://github.com/zvance1/Zach_DATA606/blob/main/Images/countOfNewConstructionPerCounty.png?raw=true)

Comparatively, the count of new construction homes looks to be favored in Anne Arundel - it has the most new construction homes and the counts of new construction there have increased over the years.  The least amount is between Harford and Howard.  New construction decreased slightly across the board in 2021 in the midst of the COVID-19 pandemic and has consistently decreased gradually in Howard county.  2022 is low again because it is not a full years worth of data.

![avgSoldPriceMinusListPrice](https://github.com/zvance1/Zach_DATA606/blob/main/Images/avgSoldPriceMinusListPrice.png?raw=true)

Looking at the above figure we see that the housing market had become much more of a sellers market as of recently.  Up until 2020 homes were selling for under their list price, then with markets becoming more competitive in 2020 with the development of the COVID-19 pandemic, residential homes have been selling at or above their list price.  This can imply that home price is dependent on more than just the features of the house - it depends on world events and market fluctuation.  So far into 2022 the average differenc ehas come down in 3 of the 4 counties, only going up in Harford.


### Machine Learning Analysis

In the machine learning analysis, the goal is to predict the sold price of a home based on its features.  It was decided to predict the sold price as it can be argued that it is the closest to the true value of the home.  The original and list prices may not be as telling as the home is only valued at what a person is willing to buy it for, not what the lister thinks it is worth.  So, in predicting home prices, the accuracy is measured as how close the predicted value is to the sold price of the home in the historical data.

Several models were experimented with to reach the goal of predicting home price; including linear regression, decision trees, Support Vector Regression, and XGBoost.  Linear Regression places weights on the features for which were analyzed to see what the model placed the highest weights on thus corresponding to being more important for predicting price, after min max scaling.  Decision trees are typically more widely used in classification problems, but good for analysis in our context here as the top level first decision will be the one it chooses to eliminate the most error and thus the factor it sees as most important for determining price.  So, by looking at the top couple of splits it is telling in terms of what its modeling sees as being the most telling about the sold price.  Support Vector Regression and XGBoost are slightly less interpretable but their workings turned out to be better for the accuracy of the model.

Beginning by looking at linear regression:

![olsRegressionSummary](https://github.com/zvance1/Zach_DATA606/blob/main/Images/olsRegressionSummary.png?raw=true)

![olsRegressionCoefficients](https://github.com/zvance1/Zach_DATA606/blob/main/Images/olsRegressionCoefs.png?raw=true)

With linear regression the model achieved a r-squared value of 0.608, telling us that approximately 61% of the variation in the sold price could be explained by the variables in the model.  Here, the variables were normalized using sklearn’s preprocessing MinMaxScaler in order to standardize the variable’s values between 0 and 1 for each, and therefore compare the coefficients to whereas the larger ones are the ones that have the higher effect on the sold price.  With that, interestingly, the variable with the highest coefficient was the number of acres the home sits on.  It is then followed by the number of garage spaces, amount of interior square feet, number of full bathrooms, number of half bathrooms, then by number of bedrooms.  The variables found to have negative coefficients also make sense intuitively – looking at the county factor, Baltimore and Harford counties are cheaper areas and thus have negative coefficients.  The value of the home is also reduced when it has no fireplace, isn’t waterfront, or isn’t new construction.  The linear regression model was run for ols, ridge and lasso to determine which performed the best over 30 iterations of different random splits of the data.  On the graph we see only 1 line because all three methods performed to the exact same r squared value when rounded to two decimal points.  When looking at the p values of the results here, all the variables included are statistically significant and proven to have an impact on the sold price.  Linear regression was also run with different variables involved, as well as one-hot-encoding the style of home which is whether it is a rancher, colonial, capecod or so on and many of those were statistically insignificant which is why it was decided to not include those in the final model here.

![decisionTree](https://github.com/zvance1/Zach_DATA606/blob/main/Images/decisionTree.png?raw=true)

With decision trees after tuning the parameters the model ended up achieving a R-Squared score of about 0.65 when using a max tree depth of 15 which is slightly better than achieved with linear regression.  Decision trees tend to be more widely used in classification instances as things are sorted into buckets rather than being continuous.  For our purposes here the main thing I wanted to get out of the decision tree was the application of which features it split on early to minimize loss early on.  Interestingly, it split on interior square feet, number of full bathrooms, and waterfront when limited to 10 leaf nodes.  The amount of interior square feet and number of full bathrooms were also highly valued in linear regression, but the waterfront feature was not as much.  Perhaps telling us that linear regression did not value waterfront as much as it should have.

![linearRegressionResiduals](https://github.com/zvance1/Zach_DATA606/blob/main/Images/linearRegressionResiduals.png?raw=true)

![supportVectorRegressionResiduals](https://github.com/zvance1/Zach_DATA606/blob/main/Images/svrResiduals.png?raw=true)

![xgboostResiduals](https://github.com/zvance1/Zach_DATA606/blob/main/Images/xgBoostResiduals.png?raw=true)

When it comes to comparing the models, the main approach was to use a combination of the R Squared values and the residual plots.  With it being a lot of data, the residual plot can be a little difficult to read since the points closer to having a residual of 0 are not so differentiable.  First, looking at the residuals for linear regression, clearly there is a pattern with it being somewhat cone-shaped where for homes that sell for less, the predictions are more accurate.  As the predicted price goes up, it gets less and less accurate.  For the support vector regression residuals, we see a little bit less of that pattern.  For both linear regression and support vector regression mostly, all predictions are within 500k of the actual price, which is not that great given most homes in the dataset are selling for less than a million dollars.  Most are more accurate than that but by the look of it, a fair number of predictions are off by a couple hundred thousand dollars.  Looking at the residuals for XGBoost, they are much better, and I achieved a R squared of .976.  There is no apparent pattern in the residuals, and most are within 50k, nearly all are within 100k, only with a few outliers.  The R squared values went from 0.609 to 0.736 to 0.923 – the XGBoost model was by far the most accurate and certainly the one to use when it comes to predicting the sold price of new homes on the market.

### Interpretations / Key Takeaways

In conclusion of interpreting the models, it appears that the most telling features for home price begin with the number of acres the home sits on and how much interior square feet it has.  This makes sense as these are the most telling features as for how much house you are getting for the price.  Secondly, the number of full bathrooms is the next most valued feature of a home.  Homes typically tend to have less bathrooms than bedrooms and it seems that a lot of value is put on a home with a good number of bathrooms.  The more bathrooms the home has, the more value it has.  A bathroom per bedroom is something that people may not find too often and is something that there seems to be a lot of demand for.  There are a relatively small number of waterfront homes compared to the total number of homes out there, and waterfront is a feature that adds a lot of value to a home.

### Interactive Interface

For simplicity, no web server was made as a user interface, but a script was created to take user input to give to the optimized XGBoost model to give a predicet price based on the user's inputs.  With this, it is an example of how the model can be used, and a start to giving the user an idea of what they should expect to pay for a home with the specified features and can compare it to homes on the market with those features to determine if they are generally under or over valued.  It leads to all kinds of possibilities in future work.  With a model like this, and recommending an optimal home based on a buyer's desires, it gives a buyer more confidence that they are getting as much for their money as they can and can be happy with what is one of the biggest purchases of their life.

### Future Work

The interface firstly should be turned into a web application.  Next, the application could be turned into a recommender.  With this, it would have the user differentiate between features that are must haves, nice to have and things that they really don’t want.  For the nice to haves, it would have them rate on a scale of 1-10 of how bad they want it, then develop an algorithm to provide them with their optimal home based on their inputs and budget.  If they can get all their must haves under their budget, great!  If not, tell them they can’t and try to get them the best balance of their nice to haves.  This could be used both as a recommender for homes that exist on the market for sale if it is up to date with the latest homes available to provide the home it thinks would be the best fit for the user; or it could be used to provide the user with what their optimal home would be under their budget.  Then, based on what the model says the buyers optimal home is they can search for something on the market to be as close to that as possible.

Another thing to do with the recommender would be to have a real estate agent use it for a time and collect data on how it does in terms of people liking the home it recommends for them.  With that, more data can be collected over time as for what kind of homes certain buyer likes and that could become its own dataset in and of itself for another machine learning application to, based on the buyers preferences, provide them with a home that people similar to them have liked.  For use of this model over time, a data pipeline should be setup so that as new historical data comes in it is added into the pipeline and thus incorporated into the model to keep the model as accurate as possible based on the latest market trends.  The pipeline could be made so that the model is updated immediately as new homes come into the multiple listing service.  More data could also be pulled in with more information such as crime rates and school districts to add those features into home price and see if it can make the model even more accurate.

### Project Structure

Data here: [Raw Data](https://github.com/zvance1/Zach_DATA606/tree/main/RawData)

Cleaned Data here: [Cleaned Data](https://github.com/zvance1/Zach_DATA606/tree/main/CleanedData)

Images here: [Images](https://github.com/zvance1/Zach_DATA606/tree/main/Images)

Trained Models here: [Models](https://github.com/zvance1/Zach_DATA606/tree/main/Models)

Python Jupyter Notebooks: [Python Jupyter Notebooks](https://github.com/zvance1/Zach_DATA606/tree/main/Notebooks)

Presentations: [Presentations](https://github.com/zvance1/Zach_DATA606/tree/main/Presentations)

Reports (HTML from Pandas): [Pandas Profiling Reports](https://github.com/zvance1/Zach_DATA606/tree/main/Reports)

