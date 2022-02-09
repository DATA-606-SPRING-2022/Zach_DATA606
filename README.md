# DATA 606 Capstone Project - Draft Proposal

# Predicting Maryland Home Prices and Finding their Value

### What is your issue of interest (provide sufficient background information)?

I would like to create a model on predicting home prices in Maryland as well as potentially finding value in certain home based on a buyers preferences.  In today's very competitive market, it is difficult for first time home buyers like myself to jump into.  Prices are high and so are desires for a home, so a model in finding homes that are undervalued or give the most value for as pertains to what the buyer can afford and wants could be a huge help and make the home decision for the buyer that much easier.  At the same time, investors may also be interested in this model as it relates to finding value in certain properties that are good for positive cash flow based on its features.

### Why is this issue important to you and/or to others?

The issue is important to me as a first time home buyer because there are so many things to consider and weighing the decisions is difficult to do.  I think seeing the price differential between home in certain areas, or certain styles, with different features will give me a better understanding of where exactly the value in a home comes from and what areas, styles, and features are most costly.  With that, I can better weigh the cost of that location, style, or feature to make a better informed decision about the home I'd like to purchase.  I think as an extension of this project, it also has the potential for me to input weights into features that I care about, say for example, I place the weight of a 10 on the location being Annapolis, but only a 3 on it having 3 bedrooms, and with that information the model could find homes with the most value based on the weights I give it.

### What questions do you have in mind and would like to answer?

The questions I have in mind are what areas, styles, and features of the home cost the most, and based on that what homes then offer the most value for their cost?  I think a lot of people try to make a decision that offers them the best value for their money.  With that, they would be very interested to the answer to the question about how to find the most value to them in the home that they buy.  Questions on what impacts the price the most - is it being on the water, the number of bedrooms, the amount of land?  Are homes pricier in certain cities?  Is there more new construction in certain areas?  Is there value in new construction over buying a pre-existing house?

### Where do you get the data to analyze and help answer your questions (creditability of source, quality of data, size of data, attributes of data. etc.)?

I plan to get the data from a real estate agent, a family member has dumped housing data for me to be able to analyze.  I put an example file in the data directory of the repo below.  The data contains fields such as category, list date, off market date, settlement date, original price, list price, sold price, address including city, state, and zip, county, school district, acres total, whether its a house for older persons, condo association, homeowners association, age, square footage, style, number of floors, whether it has a basement, garage spaces, fireplace, waterfront, new construction, number of bedrooms, and number of bathrooms among other things.  It is credible striaght from the real estate agent's dump of it, of high quality and consistent, and contains thousands of rows (not sure how many yet, will have to get more data from the agent.

Data example here: 

### What will be your unit of analysis (for example, patient, organization, or country)? Roughly how many units (observations) do you expect to analyze?

I intend to look at the data for all of Maryland.  I need to confirm with the real estate agent that I can get this data.  I expect that this will be at least 50,000 observations but need to get all the data from the agent to confirm exactly how many there will be.

### What variables/measures do you plan to use in your analysis (variables should be tied to the questions in #3)?

I plan to use the sold price as the actual price of the house to be predicted and use a combination of mostly all of the attributes listed above to try to predict that value, trying different things and seeing which of them are more significant than others.  In exploratory analysis I plan on using some of those attributes in combination with each other, for example, to answer questions like are certain styles more prevalent in some areas over others?

### What kinds of techniques/models do you plan to use (for example, clustering, NLP, ARIMA, etc.)?

I plan to use a combination of models in predicting home price - Support Vector Regression, linear regression, decision tree, random forest.  For other analysis I'd like to use k means clustering to see if certain price ranges are more prevalant in certain areas, among other possibilities of clustering by other features like home style.

### How do you plan to develop/apply ML and how you evaluate/compare the performance of the models?

I plan to test the predicted price against the sold price of the home in an effort to perform supervised machine learning on it.  For the clustering I intend to map the clusters to see if I can see a trend there.

### What outcomes do you intend to achieve (better understanding of problems, tools to help solve problems, predictive analytics with practicle applications, etc)?

I want to achieve a combination of all of those outcomes.  I think the problem to be solved is finding the value in homes.  By researching it, I can better understand the problem and all the factors into a homes value as well as understanding the values that cannot be represented on paper, tools to help solve the problem such like the one I'd like to develop, predictive analytics then follows by being able to take features of a home and place a value on it, and practicle applications where the value of a home is different to different people and if time permits I think it would be really cool to be able to allow personal input into the valuation of a home.  Perhaps to one person a $500,000 home on the water has more value than a $500,000 home not on the water.

