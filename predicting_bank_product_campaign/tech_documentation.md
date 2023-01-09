# Predicting bank products campaign outcome
1. Data Visualization
    1. Load data and view it briefly
    Load data into memory and briefly view it's shape and types. There are both numeric and categorical features in the data set. Viewing the predicted feature in detail, i.e. column "y" which is a binary category and shows whether customers have subscribed to the bank's term deposit product, I noticed the result is imbalanced, with "no" being 9 times higher than "yes".
    1. Plot data
    Here I plotted several categorical and numeric features and their interactions to understand the data set better, as well as to gain some insights in customer propensity in buying the product.
1. Data Proprocessing
    1. Check for missing values:
    I check for cells that are either null or has a value of "unknown". There's no null cells and after inspection I decided the "unknown" value might carry information so I didn't remove those data points.
    1. Check outliers
    Outliers are checked for numeric features and removed if necessary.
    1. Feature encoding
    Transform categorical data into numeric as data preparation to train the model.
    1. Split the data
    Split the data into train and test.
    1. Feature scaling
    Use standardScaler to standardize numeric features. 
1. Feature Engineering
    1. Correlation matrix
    Plot a correlation matrix to find the highly correlated features and remove them. The threshold for removal should be carefully tested. Here I use 0.95%. 
    1. Apply SMOTE for minority over sampling
    Since we discovered the predicted label is highly imbalanced, here I use SMOTE to oversample the minority class. 
    1. Apply PCA dimensionality reduction
    Run PCA to remove high dimensions.
1. Developing Models
    Now with all data preparation work done, I train three models are compare their results
    1. Create a Logistic Regression model
    1. Create a Multilayer Perceptron model
    1. Create a Random Forest model
    1. Compare results and plot them
        | | MSE | Training Score | Accuracy |
        | ----------- | ----------- | ----------- | ----------- |
        | Logistic Regression      | 0.142649       | 0.867255 | 0.857351 |
        | Multilayer Perceptron   | 0.113027        | 0.992101 | 0.886973 |
        | Random Forest   | 0.112905        | 1.0 | 0.887095 |
    Random Forest Classifier gave the highest accuracy after training the models for a few times. Although Multilayer Perceptron Classifier also has a very good performance. 
1. Conclusion
    In summary, Comparing above models, we conclude that Random Forest is the best model which is giving accuracy around 89%. Multilayer Perceptron gives a similar results and with Logistic Regression doing the poorest, which is around 85%. 
    We also have gained some insights by plotting the data:
    In general, younger customers (<40 years old) are more likely to purchase the term deposit. Education level and profession affect customers' participation. For example, people are more willing to participate in the campaign if they either hold an admins, blue-collar, or technicians job or have a university degree or high school diploma.
Repeated campaigns are more effective in some professions such as entrepreneurs
Two attempted campaigns is enough for the majority of the population.
1. Deployment
    I also included deploying this Random Forest Classifier as a web service using Flask in this section. The deployment takes input in a POST request through https://localhost:8080/predict and returns the prediction in a JSON response.