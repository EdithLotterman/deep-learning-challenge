# *Module 21 deep-learning-challenge* <br>
# Categorizing Successful Projects for Alphabet Soup Charity <br>

## Overview <br>
#### Alphabet Soup Charity has a block of data available on its past projects, and whether they were successful or not. Mnagement would like a model to help predict which projects are likely to be successful. The goal of this project was to use a neural network machine learning model to see if successful projects can be accurately determined from the other data Alphabet Soup has collected and stored on its grantees. An initial target of 75% was chosen as a good balance between funding projects likely to be successful without excluding potentially beneficial, but riskier, projects. The initial data set included:
    *EIN and NAME—Identification columns
    *APPLICATION_TYPE—Alphabet Soup application type
    *AFFILIATION—Affiliated sector of industry
    *CLASSIFICATION—Government organization classification
    *USE_CASE—Use case for funding
    *ORGANIZATION—Organization type
    *STATUS—Active status
    *INCOME_AMT—Income classification
    *SPECIAL_CONSIDERATIONS—Special considerations for application
    *ASK_AMT—Funding amount requested
    *IS_SUCCESSFUL—Was the money used effectively <br> 

## Results <br>
1. Data Preprocessing <br>
   *The data included two identification columns, EIN and name, that were immediately dropped from the data set because they had no impact on the success of the project. 
   * The Is_Successful column was used as the target column because our ultimate goal was to classify projects as successful or unsuccessful.
   * The number of unique values was reviewed for all other columns. Two, Application_Type and Classification, had over ten categories of data. These were revewied and binned to create meaningful categorization.
    ![](../Images/app_types.png)
   * The final number of features after categories were transformed for the model was 44.
   * Data was split into training and testing data, and the test data was scaled using a standard scaler.
   * After the initial model failed to achive the accuracy target, the Ask_Amt was reviewed for potential outliers. A boxplot of the data shows that most requests are clustered together as smaller requests, with a large number of data points above the third quartile. Rather than excluding all these points, a cut-off of 2 million was chosen to remove the extreme outliers from the data set. <br>
  
2. Compiling, Training, and Evaluating the Model <br>
    *A Tensorflow keras sequential model was chosen due to the complexity of the  data set. Initially two layers were chosen, with twice the number of neurons as features,  for a total of 88 in the first layer with half as many nodes in the second layer. Relu was chosen as the intial activation function. The model ran for 100 epochs. These points were chosen for being standard starting points, and to minimize memory usage with more nodes and/or layers unless necessary to improve accuracy.
    *Nodes were increased and another layer added when the initial model failed to achieve the required accuracy.
    *I experimented with using tanh as an activation function within the different layers. None of the combinations appeared to improve accuracy.
    *I did not increase epochs as the final epochs all had similar accuracy, suggesting that model performance was not likely to improve with further epochs.

## Summary <br>
I was not able to achieve the target model accuracy of 75%, although the last model just missed the target at . Next steps might include re-visiting the Ask_Amt data. This data shows a non-normal distribution, with significantly more small asks than large asks. Removing the largest outliers made the biggest improvement to model accuracy. Perhaps removing all outliers outside of the 1.5 IQR would improve model accuracy, as long as it is clear to Alphabet's management that the model is only accurate at predicting smaller ask amounts. Adding a layer and more nodes also improved model performance very slightly, but changing the activation function appeared to have no impact. Another next step would be to use hyperparameter tuning to determine the exact best parameters. I did not adjust the number of epochs as the final epock numbers all appeared to be very similar. Another next step would be to try a simpler model, such as a logistic or tree forest model. Teh confusion matrix might help to narrow which classifications the model is struggling with ot help with better data prep<Br>


