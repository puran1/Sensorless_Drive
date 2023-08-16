# Sensorless_Drive
Study of Sensorless Drive Diagnosis dataset collected from UCI website
This is an attempt to analyze the data and then use different classification methods to evaluate which methods perform well for the “Dataset for Sensorless Drive Diagnosis”. This dataset is available in UCI Machine Learning Repository at https://archive.ics.uci.edu/dataset/325/dataset+for+sensorless+drive+diagnosis
In a brief, features are extracted from electric current drive signals. The drive has intact and defective components. That results in 11 different classes. It has 49 attributes – out of which 48 are considered features. The attribute with 11 different classes is considered as target variable. Both features and target variable do not have name.
1.	Data Overview
Since the features and target variable do not have name, so for data analysis purpose we name features as “A1”, “A2”, “A3”, …, “A46”, “A47”, “A48”. Next, we name the target variable as “Class”.
The dataset has 58,509 rows. None of the features have missing values.
2.	Exploratory Data Analysis
Except the “Class” column all the feature columns have decimal numbers.
2.1.	 Class in Data
There are 11 classes in “Class” column and all the classes are equally distributed
2.2.	Variable Distribution
We need to check whether some features are correlated to each other. We use Pandas Pearson correlation coefficient function corr() to determine the relation among different features.
3.	Data Preprocessing
We select features which have Pearson Coefficient greater than 0.9 with another feature as highly co related and drop from the list of features. “A7”, “A8”, “A10”, “A11”, “A13”, “A16”, “A19”, “A20”, “A21”, “A22”, “A23”, “A31”, “A32”, “A34”, “A35”, “A43”, “A44”, “A46”, “A47” are dependent on other features. So, it can be dropped. The dropping of the above columns do not change the distribution of “Class” column. The “Bar” diagram shows the distribution of different values of “Class”.

  3.1.	Separating Independent and Dependent Variables
           
   To analyze the data we create a matrix of independent variables which have 29 columns and “Class” is dependent variable.
   
  3.2.	Encoding the Dependent Variable
          
   Used label encoder to encode dependent variable to start at value 0 instead of 1
   
   3.3.	Splitting the dataset into the Training set and Test set

   We divide both independent and dependent variables to Training Set and Test Set
   
   3.4.	Since independent variables have different scales, so we use feature scaling to make the data uniformly scaled.
   
   3.5.	Variable Summary

   Next, we evaluate summary – count, mean, standard variation, minimum, 25, 50, 75 percentile, and maximum of each feature.
   
   3.6.	Correlation Matrix

   The relation among the features are depicted through Correlation Matrix

4.	Model Building

    4.1.	Baseline Model

    Performance of Logistic Regression classifier: Accuracy Score is 0.744 and Area under the curve is 0.962. “A9” is the most influential feature, followed by “A4”. 

  	 4.2.	Recursive Feature Elimination

          Performance of Logistic Regression classifier with feature elimination: Accuracy Score is 0.744 and Area under the curve is 0.962. “A9” is the most influential feature, followed by “A4” in this case as well.
  	
    4.3.	Decision Tree Classifier

          Performance of Decision Tree classifier: Accuracy Score is 0.967 and Area under the curve is 0.997. “A12” is the most influential feature, followed by “A9”.
     4.4.	KNN Classifier

          Performance of K-Nearest Neighbor classifier: Accuracy Score is 0.667 and Area under the curve is 0.922.
      4.5.	Random Forest Classifier

            Performance of Random Forest classifier: Accuracy Score is 0.983 and Area under the curve is 1.0. “A12” is the most influential feature, followed by “A9”.
       4.6.	Gaussian Naïve Bayes

            Performance of Naïve Bayes classifier: Accuracy Score is 0.648 and Area under the curve is 0.974. 
       4.7.	Support Vector Machine

            4.7.1.	Support Vector Machine (linear)

                    Performance of Support Vector Machine (linear) classifier: Accuracy Score is 0.926 and Area under the curve is 0.995. “A9” is the most influential feature, followed by “A4”.
            4.7.2.	Support Vector Machine (non-linear:rbf)

                    Performance of Support Vector Machine (rbf) classifier: Accuracy Score is 0.952 and Area under the curve is 0.998. 
       4.8.	LightGBM Classifier

               Performance of Light GBM classifier: Accuracy Score is 0.992 and Area under the curve is 1.0. “A12” is the most influential feature, followed by “A9”.
       4.9.	XGBoost Classifier

            Performance of Xtreme Boost classifier: Accuracy Score is 1.0 and Area under the curve is 1.0. “A12” is the most influential feature, followed by “A9”.
       4.10.	AdaBoost Classifier

              Performance of Ada Boost classifier: Accuracy Score is 0.311 and Area under the curve is 0.698. “A12” is the most influential feature, followed by “A9”.
       4.11.	GradientBoosting Classifier

              Performance of Gradient Boosting classifier: Accuracy Score is 0.996 and Area under the curve is 1.0. “A12” is the most influential feature, followed by “A9”.
       4.12.	Linear Discriminant Analysis

              Performance of Linear Discriminant Analysis: Accuracy Score is 0.839 and Area under the curve is 0.987.
       4.13.	Quadratic Discriminant Analysis

               Performance of Quadratic Discriminant Analysis: Accuracy Score is 0.819 and Area under the curve is 0.993.
       4.14.	Multi-layer Perceptron Classifier

             Performance of Multi-layer Perception classifier: Accuracy Score is 0.813 and Area under the curve is 0.979.
       4.15.	Bagging Classifier

              Performance of Bagging classifier: Accuracy Score is 0.991 and Area under the curve is 0.999.
6.	Model Performances over the Training Dataset

    5.1.	Model Performance Metrics

          From the tabular representation of the metrics of the classifier used in this analysis, it is clear that XGBoost Classifier performed the best followed by Gradient Boost. While Ada 
          Boost classifier performed the worst.
     5.2.	Compare Model Metrics

          Bar graph presentation of the performance shows the observation we made in section 5.1.
     5.3.	Confusion Matrices for Models

          Heat map representation of the Confusion Matrix shows the deviation of values from the top left to bottom right diagonal.
7.	Model Performances over the Test Dataset

     6.1.	Model Performance Metrics

          From the tabular representation of the metrics of the classifier used in this analysis, as in the case of Training Dataset, it is clear that XGBoost Classifier performed the best followed by 
          Gradient Boost. While Ada Boost classifier performed the worst.
    6.2.	Compare Model Metrics

          Bar graph presentation of the performance shows the observation we made in section 6.1.
     6.3.	Confusion Matrices for Models

           Heat map representation of the Confusion Matrix shows the deviation of values from the top left to bottom right diagonal which are similar to the Training Dataset

