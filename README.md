# Predictive-analysis-on-Titanic-dataset

Here is an expanded summary report with relevant headings for the Titanic survival prediction code:

# Titanic Survival Prediction

## Data Loading and Inspection

The data is loaded from a CSV file into a Pandas DataFrame. The head() method is used to inspect the first few rows and get an idea of the features. Columns like Name, Ticket, Cabin etc are dropped as they don't seem useful for prediction.

## Exploratory Data Analysis 

Summary statistics like df.isnull().sum() and df.shape are used to analyze the data. This shows that features like Age and Cabin have missing values that need to be handled.

## Feature Engineering

### Encoding Categorical Variables

The Sex feature is label encoded to numeric categories using sklearn's LabelEncoder. This converts the male/female strings to 0/1 encoding.

### Imputing Missing Values

The Age column has around 20% missing values. KNNImputer is used to fill these based on similarities with other samples.

### Feature Scaling

Age and Fare are scaled to [0,1] range using MinMaxScaler. This normalization is useful for many models like SVM.

## Handling Class Imbalance

The target class (Survived) has imbalance between 0 and 1 labels. To fix this, the majority class (those who did not survive) is undersampled to match the minority class size.

## Model Training and Evaluation

### Hyperparameter Tuning

GridSearchCV is used to tune the C and kernel hyperparameters of an SVM model via cross-validation. Linear and RBF kernels are evaluated.

### Model Selection

The best SVM model with RBF kernel and C=50 is selected based on having the highest cross-validation accuracy.

### Model Boosting

The SVM model is boosted using XGBoost to create an ensemble. This further improves the accuracy.

### Performance

The final boosted model achieves 82% accuracy on the test set, significantly better than the base SVM model. The confusion matrix is also printed.

## Conclusion

Key techniques like handling imbalance, feature engineering, hyperparameter tuning and model boosting helped create an accurate model for this binary classification problem. The code can serve as a template for other tabular classification tasks.
