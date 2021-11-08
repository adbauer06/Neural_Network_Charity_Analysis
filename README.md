# Neural_Network_Charity_Analysis

## Overview of Analysis
The purpose of this analysis was to use machine learning, specifically a neural network, to create a binary classifier that is capable of predicting with a high level of accuracy whether an applicant will be successful if funded by Alphabet Soup.  

In order to create and train our model, we used the charity_data.csv dataset which contains information for more than 34,000 organizations that have recieved funding from Alphabet Soup over the years, including information about each organization, amount of funding requested, and whether their funding given was used effectively.

For this analysis, we preprocessed the data to remove any unnecessary columns as well as condense column information where it was beneficial.  We updated all of the categorical data to numerical, as well as scaled the data to make it more standardized.  Once our data was ready, we created our model, trained it, and evaluated its performance.  We then attempted to optimize it to improve our accuracy in predicting whether an organization will be successful or not.


## Results
### Data Preprocessing
- Our target variable for our model is "IS_SUCCESSFUL", whether or not the applicant will be successful if funded by Alphabet Soup.
- Our feature variables for our model are:
    - "APPLICATION_TYPE"
    - "AFFILIATION" (affiliated sector of industry)
    - "CLASSIFICATION" (government organization classification) 
    - "ORGANIZATION" (organization type)
    - "STATUS" (active or not) 
    - "INCOME_AMT"
    - "SPECIAL_CONSIDERATIONS"
    - "ASK_AMT"
- The following variables are neither targets or features and were removed to clean up the input data:
    - "EIN"
    - "NAME"
    - "USE_CASE" (Use case for funding)

### Compiling, Training, and Evaluating the Model
- Initially I created a model that had an input layer, 2 hidden layers, and an output layer.
- I started with 80 neurons in the first hidden layer and 30 neurons in the second hidden layer.  I chose to start with 80 neurons in the first hidden layer as that was about twice the number of input parameters I had.  The 30 in the second layer was just chosen as a starting point.
- I chose to use the "Relu" activation function for all but the output layer, in which case I chose to use "Sigmoid".  Sigmoid is ideal for use with binary classification.  Relu is also a good activation function for classification and does well with non-linear postive input data.
- The initial model created did not have an exceptionally high accuracy rate, around 72%.
![Accuracy_for_initial_model.png](Resources/Accuracy_for_initial_model.png)


- The following steps were taken to try and optimize the model to achieve the target performance of 75% accuracy:
    - Removing other unnecessary columns, in this case "USE_CASE" did not seem like it would have an impact on funding success.  However, rerunning the model after removing that column did not show any noticeable improvement.
    
        ![Accuracy_attempt1_optimization.png](https://github.com/adbauer06/Neural_Network_Charity_Analysis/blob/main/Resources/Accuracy_attempt1_optimization.PNG)

    - A second attempt at optimization included increasing the number of neurons in the two existing hidden layers as well as adding an additional hidden layer.  This also did not produce any noticeable improvement.
    
        ![Accuracy_attempt2_optimization.png](https://github.com/adbauer06/Neural_Network_Charity_Analysis/blob/main/Resources/Accuracy_attempt2_optimization.PNG)
    
    - A third attempt at optimization included experimenting with a different activation function.  Again, rerunning the model showed no significant improvement.
    
        ![Accuracy_attempt3_optimization.png](https://github.com/adbauer06/Neural_Network_Charity_Analysis/blob/main/Resources/Accuracy_attempt3_optimization.PNG)


## Summary
In summary, this model did not perform exceptionally well, with just a 72% accuracy score.  Although we made several attempts to optimize it, none of them were successful.  

I would recommend taking a closer look at the data coming into the model to see if it can be cleaned further.  In particular, I would look at the ASK_AMT column.  We did not do anything with that since it was a numeric column already, but I think it would be worth trying to see if binning that data into category ranges, if reducing the number of unique values in that column would improve model performance.  From there I would create a new model to process that file, and then further experiment with adding or removing neurons and hidden layers, as well as try other activation functions.

Otherwise, if we wanted to try a model different than the deep learning model, I would recommend trying a Random Forest classifier as an alternative.  They are scalable, able to handle non-linear data and seem to have similar processing power as a deep learning model.

