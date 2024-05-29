# Customer Support Ticket Analysis for Improving Customer Feedback

## A note for those who look through this project..
This project, if submitted to a higher up to be implemented into an overarching customer service operation, would be utterly laughed at and I would be fired. I am unable to obtain an accuracy score of above 25% for this project. So why do I keep it in? Because I like to think it's a showcase of my ability to continue trying even when I fail. This project is the answer when an interviewer asks "tell me about a time you failed". Enjoy reading through!

## Project Overview
In this project, I will be working with a Customer Support Ticket dataset that includes customer support tickets for various tech products. This dataset contains customer inquiries related to hardware and software issues, network problems, account access, data loss, and other support topics. It also provides information about the customer, when they purchased the product, what type of ticket, the ticket channel, status, and any other relevant details.

For the analysis, I will be using natural language processing to automate ticket categorization and sentiment analysis. Splitting the data into training and test sets, I will turn the ticket description into token words, then use Tifid Vectorization to use in analysis. From the variables provided by the dataset, ticket priority will be the target variable. I will use ticket subject, product type, and the token words from the ticket description to determine the priority of the ticket. Ticket priority will tell the critical nature of the ticket, allowing the customer support team to know whether the ticket needs to be prioritized.

# Data Preprocessing
This dataset is available on [Kaggle](https://www.kaggle.com/datasets/suraj520/customer-support-ticket-dataset).
There are 8,469 row entries and 18 columns to this dataset. 
I create a datetime object for the First Response Time variable and the Time to Resolution variable. I drop unnecessary features, like customer name and email. Then I create a subset of the data of just ticket ID, Ticket priority, and ticket description.

Next, I tokenize the words in the ticket description. 

## Modeling & Evaluation
Using a Tfidf Vectorizer, I convert the words to td-idf vectors for modeling purposes. For cross-validation, I split the data into a training and test set. I utilize a multinomial Logistic Regression model, but I end up with an accuracy of 25%. I attempt to improve this accuracy score using Grid Search, using a variety of values for C to determine the best one for the model. 
This returns an accuracy score that increases by 0.2% unfortunately.

Next, I try a Random Forest Model to determine if I will have more luck. UNfortunately, this only increases the accuracy to 25.8%. 

## New approach... 

The models I have produced thus far are hardly more accurate than random guessing. This indicates I may need to adjust the features in the model to allow for more accurate predicting. I will create a new dataframe, and add quite a few more features, including Ticket Subject, Ticket Type, Product Purchased, Gender, Age, and the token words from earlier (as long as they do not cause too much issue being text based).

The models I have produced thus far are hardly more accurate than random guessing. This indicates I may need to adjust the features in the model to allow for more accurate predicting. I will create a new dataframe, and add quite a few more features, including Ticket Subject, Ticket Type, Product Purchased, Gender, Age, and the token words from earlier (as long as they do not cause too much issue being text based), which turns an accuracy of yet again 25.54%. 

What happens if I take out the token words? The accuracy drops to 24.55%.  I will try ordinal regression since the ticket priority is ordinal in nature.

This returns the lowest accuracy score yet of 23.45%!

I try the SVM model one more time with extra features to only return a value of 24.55%.


## Conclusion
I have tried many different models, added in several different features to possibly get the model to be more accurate than just random guessing. There might be more information not included in this dataset that can predict whether a ticket needs to be escalated, like whether the customer is at risk for churning, if there is an influence of stakeholders, etc. While the model creation may not have been successful at prediction, this is a problem that can be worked at given more time to obtain more accurate results.
