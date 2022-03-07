# DATA 606 Capstone Project - Proposal

# Predicting Maryland Home Prices and Finding their Value


Initial Presentation here: [EDA V1.2 Presentation](https://youtu.be/M-Pc2erqVoM)


### Background Information

This project is to create a model on predicting home prices in Maryland, more specifically in Anne Arundel, Harford, Baltimore, and Howard counties.  I also have an interest in finding a way to place weights on the values of certain homes based on a buyers preferences, if time permits me to do so.  In today's very competitive market, it is difficult for first time home buyers like myself to jump into.  I'm planning on purchasing a home in 2023 and a model like this could prove valuable to me and all the others buying a home in the next year.  Prices are high and so are desires for a home, so a model in finding homes that are undervalued or offer the most based on a buyer's preferences gives the buyer the best house for their money.  Buying a home is one of the biggest purchases people will make in their life, making it a tough decision.  The model I'd like to create I feel would give the home buyer more confidence in their decision that they are getting a good value thus making it easier for them to know what they want, at what price, and be able to make an offer quickly and confidently.  Investors may also be interested in this model as it relates to finding value in certain properties that are good for positive cash flow based on its features.

The issue is important to me as a first time home buyer because there are so many things to consider and weighing the decisions is difficult to do.  I think seeing the price differential between homes in certain areas, certain styles, and with different features will give me a better understanding of where exactly the value in a home comes from and what areas, styles, and features are most costly.  I and many other home buyers, in our heads, place different values on different features of a home and need ot understand what that means in terms of our budget.  For example if I really want to live waterfront, how much does that cost vs a new construction home not on the water and with 1,000 more square feet than I'd have in the waterfront home?  From that I can better determine if I think the cost of living on the water is worth it in comparison to a nicer home not on the water for the same budget.  I can also uncover things like whether or not waterfront homes appreciate faster, and maybe that helps me feel more comfortable with the purchase of the waterfront home if I decide I value that more.  All in all, uncovering facts like this and being able to weigh the different features of a house more effectively is important to me and anyone else buying a home.  A finding such as waterfront homes appreciating faster, and in a certain area would also prove very useful to investors looking to profit from appreciation.  I think if I found time for it as well, like I mentioned above, if I could make a model that takes in a weight for each feature the buyer values and their budget and outputs the list of houses that offer them the best value in descending order that would prove extremely useful.

### About the Data

A family member real estate agent dumped housing data for me to be able to analyze.  The raw data I put an example file in the data directory of the repo below.  The max the real estate agent could dump was 5,000 rows per file, so I have 20 total files, containing a cumulative 90,758 homes of which were sold in the counties of Anne Arundel, Harford, Baltimore and Howard over the last 5 years.  The data contains fields such as:
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
  - whether or not it has a basement
  - garage spaces
  - fireplace
  - waterfront
  - whether or not it is new construction
  - number of bedrooms
  - number of bathrooms

Among other attributes as well.  It is credible, straight from the real estate agent's dump of it, of high quality and consistent. 

Data here: [Raw Data](https://github.com/zvance1/Zach_DATA606/tree/main/RawData)

Cleaned Data: [Cleaned Data Sets](https://github.com/zvance1/Zach_DATA606/tree/main/CleanedData)

My unit of analysis will be individual homes.  Again, targeting Anne Arundel, Harford, Baltimore, and Howard counties for historical anlysis and future predictions.

### Questions to be Answered

The biggest question I'd like to answer is what areas, styles, and features of the home cost the most, and based on that what homes then offer the most value for their cost?  I think a lot of people try to make a decision that offers them the best value for their money.  With that, they would be very interested to the answer to the question about how to find the most value to them in the home that they buy.  Below is a summary of the questions to answer:

Key question to answer:
  - What impacts the price the most?  With an ranking of features that have the largest impact on price.

Exploratory Questions:
  - What is the best month to buy a house in?
  - Have home prices gone up faster in certain areas over others?
  - How much do waterfront homes cost in comparison to non-waterfront?
  - Has the number of acres for new construction homes gone down over time?
  - How much does new construction cost in comparison to non new construction?
  - Is there more new construction in certain areas?
  - Did homes tend to go more above or below listing price during any specific time period?
  
### Initial EDA Analysis

In my intial EDA analysis I have used pyspark to query the data in order to answer the desired questions.

Begining with the question of whether or not home prices have gone up faster in certain areas over others:

![PricePerCountyPerMonth](https://github.com/zvance1/Zach_DATA606/blob/main/Images/PricePerCountyPerMonth.png?raw=true)

From the above chart we can easily see that Howard county is the most expensive, followed by Anne Arundel, then by both Harford and Baltimore being similar price levels.  Interestingly, the price movements up and down seem to follow the same trend over the course of the year.  As the price in Howard goes up towards the summer months, so does the price in Anne Arundel and the other counties, at about the same rate as well.  Based on this visualization it seems that prices for houses are the lowest in February and March of each year.

![PricePerCountyPerYear](https://github.com/zvance1/Zach_DATA606/blob/main/Images/PricePerCountyPerYear.png?raw=true)

From the above chart we can easily see the upward trend in the cost of house prices over the years.  We see again the same ordering of price levels of the 4 counties and increases at similar rates.  Home prices look to have peaked in 2021 and have so far leveled off or decreased slightly so far into 2022.

![medianPricePerWaterfrontPerCounty](https://github.com/zvance1/Zach_DATA606/blob/main/Images/medianPricePerWaterfrontPerCounty.png?raw=true)

Looking at the above chart, it is clear that Anne Arundel County waterfront homes look to have increased pretty dramatically from 2019 to 2021.  When looking at 2022, I would engourage to see it as valuable information but at the same time not to the same extent as the other years as there is not as much data for it only two months into the year (Howard hasn't had any waterfront home sales yet this year).  In Anne Arundel county, the price difference between the medians of waterfront and non waterfront is also pretty significant with the median for non waterfront being down around 400k and waterfront up over 1 million.  The cheapest is non waterfront in Baltimore county, and the difference between waterfront and non waterfront in Baltimore county is not as significant.  Waterfront is consistently more expensive than non waterfront in all of the counties, but to different degrees.

![medianAcresPerNewConstructionPerCounty](https://github.com/zvance1/Zach_DATA606/blob/main/Images/medianAcresPerNewConstructionPerCounty.png?raw=true)

In the above chart we see that there has been a slight downward trend in the size of new construction lots, more steadily for Anne Arundel and Baltimore counties.  The median in those counties has stayed in the 0.2 acre range, and that is already really small so it makes sense that the downward trend has only been slight - it is tough to get much smaller than that.  Interestingly, Howard, which we saw as the most expensive, and Harford, which we saw as the least expensive alongside Baltimore County look to have their new construction lot sizes be slightly larger, and the downward trend is not as clear or evident for those counties.  Howard and Harford counties have more land, so it will be interesting to see where the price difference between the two comes from whether it be mainly rooted in location or if homes in Howard tend to be larger than that of Harford.  For Howard, in 2022, there have only been 5 new construction home sales, 3 of which were 1 acre lots, the other 2 being 0.14 and 0.24 acres, so I'd expect that as we get further into 2022 that number come down.  Harford and Howard also have a lesser volume of homes than Anne Arundel and Baltimore counties, making their numbers less consistent.

![medianPricePerNewConstructionPerCounty](https://github.com/zvance1/Zach_DATA606/blob/main/Images/medianPricePerNewConstructionPerCounty.png?raw=true)

Here we see that new construction is consistently more expensive than non new construction in each and every county, to different degrees in each county.  Again Baltimore, non new construction shows as the cheapest option and we see Howard new construction as the most expensive option.  This is consistent with the overall average prices we saw per county earlier in the analysis and the same general increase in prices across the board.

![countOfNewConstructionPerCounty](https://github.com/zvance1/Zach_DATA606/blob/main/Images/countOfNewConstructionPerCounty.png?raw=true)

Comparatively, the count of new construction homes looks to be favored in Anne Arundel - it has the most new construction homes and the counts of new construction there have increased over the years.  The least amount is between Harford and Howard.  New construction decreased slightly across the board in 2021 in the midst of the COVID-19 pandemic and has consistently decreased gradually in Howard county.  2022 is low again because it is not a full years worth of data.

![avgSoldPriceMinusListPrice](https://github.com/zvance1/Zach_DATA606/blob/main/Images/avgSoldPriceMinusListPrice.png?raw=true)

Looking at the above figure we see that the housing market had become much more of a sellers market as of recently.  Up until 2020 homes were selling for under their list price, then with markets becoming more competitive in 2020 with the development of the COVID-19 pandemic, residential homes have been selling at or above their list price.  This can imply that home price is dependent on more than just the features of the house - it depends on world events and market fluctuation.  So far into 2022 the average differenc ehas come down in 3 of the 4 counties, only going up in Harford.


### Structure of Analysis

I plan to use the sold price as the actual price of the house to be predicted and use a combination of mostly all of the attributes listed above to try to predict that value, trying different things and seeing which of them are more significant than others.  In exploratory analysis I plan on using some of those attributes in combination with each other, for example, to answer the question of whether or not homes were selling above asking price more so for a certain time than other times, I group by month, and take the average selling price - asking price per month then graph the result to see the answer to the question.

I plan to use a combination of models in predicting home price - Support Vector Regression, linear regression, decision tree, random forest.  With these I will be able to output information about how each of the features are used within the models.  Regression will place weights on the features for which I can analyze to see what the regression models placed the highest weights on thus corresponding to being more important for predicting price.  In the decision trees, the top level first decision will be the one it chooses to eliminate the most error and thus the factor it sees as most important for determining price.  The factors being ranked by the levels of the tree and /or forest (collection of decision trees).  In other analysis, I'd like to use k means clustering to see if certain price ranges are more prevalant in certain areas.  I could run k means clustering on all the homes, or on select homes specifically to try to keep their features relatively constant to narrow down on what areas are the priciest for a similar home.

Like I mentioned previously, I plan to test the predicted price against the sold price of the home in an effort to perform supervised machine learning on it.  I will measure the accuracy/ performance of the model based on how close the predicted value is to the actual sale price of the home.  To do this I will train the model with cross fold validation in numerous ways to see what gives me the best results.  To evaluate the performance of the clustering models, I intend to map the results as color coded points on top of the map of the counties so that trends in home price can be seen based on points on a map.  To evaluate whether or not the resulting clusters make sense I can use some of my knowledge on what I expect the results to be based on my exploratory analysis to see if the clusters formed make sense.

### Intentded Outcomes

I want to achieve a combination of all of those outcomes.  I think the overarching problem of everything mentioned here is how best to find the most value in homes for perspective home buyers.  Via the predicting of home prices I can perform predictive analytics while using the results to gain a better understanding of the problem.  I'll be able to visualize which factors of the home have the biggest effect on its cost.  Another thing I think I will find is that there may be plenty of error, different people place different values on homes and the sale price may not be a 100% good true value number.  There may also be factors that are not be captured well in the data such as the current condition of the home, whether it has well water or public, and so on.  What I'm creating is a tool to help solve the problem, and I think gaining a better understanding of the problem by running predictive analytics accomplishes that goal and I, as well as anyone reading this will learn a lot about home values and key factors involved.

### Project Structure

Data here: [Raw Data](https://github.com/zvance1/Zach_DATA606/tree/main/RawData)

Cleaned Data here: [Cleaned Data](https://github.com/zvance1/Zach_DATA606/tree/main/CleanedData)

Images here: [Images](https://github.com/zvance1/Zach_DATA606/tree/main/Images)

Python Jupyter Notebooks: [Python Jupyter Notebooks](https://github.com/zvance1/Zach_DATA606/tree/main/Notebooks)

Presentations: [Presentations](https://github.com/zvance1/Zach_DATA606/tree/main/Presentations)

Reports (HTML from Pandas): [Pandas Profiling Reports](https://github.com/zvance1/Zach_DATA606/tree/main/Reports)


### Current Status

I feel I have again made good progress on this in the past week.  I added a bunch more EDA analysis and have answered all 7 of the questions that I had listed.  I can further improve on this EDA in the next week by potentially converting counts into percentages to get a better sense of whether certain areas have more new construction, respectively.  I also wouldn't mind creating a correlation matrix between the variables to see if there are any that are highly coordinated before I get into the machine learning in the next phase.


