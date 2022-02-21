# DATA 606 Capstone Project - Proposal

# Predicting Maryland Home Prices and Finding their Value


### Background Information

This project is to create a model on predicting home prices in Maryland, more specifically in Anne Arundel, Harford, Baltimore, and Howard counties.  I also have an interest in finding a way to place weights on the values of certain homes based on a buyers preferences, if time permits me to do so.  In today's very competitive market, it is difficult for first time home buyers like myself to jump into.  I'm planning on purchasing a home in 2023 and a model like this could prove valuable to me and all the others buying a home in the next year.  Prices are high and so are desires for a home, so a model in finding homes that are undervalued or offer the most based on a buyer's preferences gives the buyer the best house for their money.  Buying a home is one of the biggest purchases people will make in their life, making it a tough decision.  The model I'd like to create I feel would give the home buyer more confidence in their decision that they are getting a good value thus making it easier for them to know what they want, at what price, and be able to make an offer quickly and confidently.  Investors may also be interested in this model as it relates to finding value in certain properties that are good for positive cash flow based on its features.

The issue is important to me as a first time home buyer because there are so many things to consider and weighing the decisions is difficult to do.  I think seeing the price differential between homes in certain areas, certain styles, and with different features will give me a better understanding of where exactly the value in a home comes from and what areas, styles, and features are most costly.  I and many other home buyers, in our heads, place different values on different features of a home and need ot understand what that means in terms of our budget.  For example if I really want to live waterfront, how much does that cost vs a new construction home not on the water and with 1,000 more square feet than I'd have in the waterfront home?  From that I can better determine if I think the cost of living on the water is worth it in comparison to a nicer home not on the water for the same budget.  I can also uncover things like whether or not waterfront homes appreciate faster, and maybe that helps me feel more comfortable with the purchase of the waterfront home if I decide I value that more.  All in all, uncovering facts like this and being able to weigh the different features of a house more effectively is important to me and anyone else buying a home.  A finding such as waterfront homes appreciating faster, and in a certain area would also prove very useful to investors looking to profit from appreciation.  I think if I found time for it as well, like I mentioned above, if I could make a model that takes in a weight for each feature the buyer values and their budget and outputs the list of houses that offer them the best value in descending order that would prove extremely useful.

### Questions to be Answered

The biggest question I'd like to answer is what areas, styles, and features of the home cost the most, and based on that what homes then offer the most value for their cost?  I think a lot of people try to make a decision that offers them the best value for their money.  With that, they would be very interested to the answer to the question about how to find the most value to them in the home that they buy.  Below is a summary of the questions to answer:

Key question to answer:
  - What impacts the price the most?  With an ranking of features that have the largest impact on price.

Exploratory Questions:
  - Have home prices gone up faster in certain areas over others?
  - Has the number of acres for new construction homes gone down over time?
  - Is there more new construction in certain areas?
  - Did homes tend to go more above or below listing price during any specific time period?
  - How much do waterfront homes cost in comparison to non-waterfront?
  - How much does new construction cost in comparison to non new construction?


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

Data here: [Raw Data](https://github.com/zvance1/Zach_DATA606/tree/main/data)

My unit of analysis will be individual homes.  Again, targeting Anne Arundel, Harford, Baltimore, and Howard counties for historical anlysis and future predictions.

### Structure of Analysis

I plan to use the sold price as the actual price of the house to be predicted and use a combination of mostly all of the attributes listed above to try to predict that value, trying different things and seeing which of them are more significant than others.  In exploratory analysis I plan on using some of those attributes in combination with each other, for example, to answer the question of whether or not homes were selling above asking price more so for a certain time than other times, I group by month, and take the average selling price - asking price per month then graph the result to see the answer to the question.

I plan to use a combination of models in predicting home price - Support Vector Regression, linear regression, decision tree, random forest.  With these I will be able to output information about how each of the features are used within the models.  Regression will place weights on the features for which I can analyze to see what the regression models placed the highest weights on thus corresponding to being more important for predicting price.  In the decision trees, the top level first decision will be the one it chooses to eliminate the most error and thus the factor it sees as most important for determining price.  The factors being ranked by the levels of the tree and /or forest (collection of decision trees).  In other analysis, I'd like to use k means clustering to see if certain price ranges are more prevalant in certain areas.  I could run k means clustering on all the homes, or on select homes specifically to try to keep their features relatively constant to narrow down on what areas are the priciest for a similar home.

Like I mentioned previously, I plan to test the predicted price against the sold price of the home in an effort to perform supervised machine learning on it.  I will measure the accuracy/ performance of the model based on how close the predicted value is to the actual sale price of the home.  To do this I will train the model with cross fold validation in numerous ways to see what gives me the best results.  To evaluate the performance of the clustering models, I intend to map the results as color coded points on top of the map of the counties so that trends in home price can be seen based on points on a map.  To evaluate whether or not the resulting clusters make sense I can use some of my knowledge on what I expect the results to be based on my exploratory analysis to see if the clusters formed make sense.

### Intentded Outcomes

I want to achieve a combination of all of those outcomes.  I think the overarching problem of everything mentioned here is how best to find the most value in homes for perspective home buyers.  Via the predicting of home prices I can perform predictive analytics while using the results to gain a better understanding of the problem.  I'll be able to visualize which factors of the home have the biggest effect on its cost.  Another thing I think I will find is that there may be plenty of error, different people place different values on homes and the sale price may not be a 100% good true value number.  There may also be factors that are not be captured well in the data such as the current condition of the home, whether it has well water or public, and so on.  What I'm creating is a tool to help solve the problem, and I think gaining a better understanding of the problem by running predictive analytics accomplishes that goal and I, as well as anyone reading this will learn a lot about home values and key factors involved.

### Project Structure

Data here: [Raw Data](https://github.com/zvance1/Zach_DATA606/tree/main/data)

Data accumulated into one file: [Appended Data](https://github.com/zvance1/Zach_DATA606/tree/main/appended_data)

Cleaned Data here: [Cleaned Data](https://github.com/zvance1/Zach_DATA606/tree/main/cleaned_data)

Python Scripts to append and clean the data: [Python Cleaning Scripts](https://github.com/zvance1/Zach_DATA606/tree/main/python_cleaning_scripts)

Python exploratory data analysis scripts here: [Python EDA Scripts](https://github.com/zvance1/Zach_DATA606/tree/main/python_eda_scripts)


### Current Status and Initial EDA Results
I haven't had the most time for this since class ended on Wednesday, I anticipate spedning more time on it in the coming week.  I had not written any code prior to class ending Wednesday so I have successfully read it in and appended it together and saved that as one file in its own directory.  I also confirmed with the real estate agent that the data is good to be public.  I need to do more on cleaning the data, I ran pandas profiling on it and every column contains null values so I'll need to find ways to deal with them.  I also need to clean up the types, where I want dollar values coming in as integers rather than strings.  I began writing queries in the eda jupyter notebook that I setup and was running into issues with my queries.  I think most likely because of the types when reading in the data, I need to clean it better first.  Definitely progress made, and I think a lot more progress will be made in the next week.




