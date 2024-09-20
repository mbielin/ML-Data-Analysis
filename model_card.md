# Model Card

See the [example Google model cards](https://modelcards.withgoogle.com/model-reports) for inspiration. 

## Model Description

Input:
The model was trained on historical data obtained from a swim club company, covering the last five years of trading across multiple locations. The data included information about member demographics (such as age and membership status), lesson participation history (with PreSchool and Academy lessons), and discounts applied. Key input features included:

Age_joined
Age_at_last_lesson
TOTAL QUANTITY OF LESSONS
Variance to Median (VTM) for PreSchool and Academy lessons
Various discount columns (e.g., SIBLING DISCOUNT APPLIED, PROMOTIONS APPLIED)
Output:
The model predicts the number of future swimming lessons a member is expected to take. For certain models (e.g., Logistic Regression), it predicts a binary outcome for whether a member is likely to take more than a specific number of future lessons.

Model Architecture:
We tested and compared the following models:

Random Forest Regression: A tree-based ensemble method with 100 estimators.
XGBoost Regression: A gradient-boosting method optimized with a learning rate of 0.1 and max depth of 5.
Linear Regression: A simple linear approach to model the relationship between input features and future lessons.
Logistic Regression: Used for binary classification of future lessons.
Artificial Neural Networks (ANNs): Two versions:
The first with two hidden layers (64 and 32 neurons) using ReLU activation.
The second with deeper layers (128, 64, 32 neurons), using a mix of tanh and ReLU activations.

## Performance

Evaluation Metrics:

Mean Squared Error (MSE): Measures how close predictions are to actual future lessons.
R-squared (R²): Explains the variance captured by the model.
Performance Summary:
Random Forest Regression: MSE ≈ 0.33, R² ≈ 0.98
XGBoost Regression: MSE ≈ 0.30, R² ≈ 0.99
ANN (first model): MSE ≈ 0.10, R² ≈ 0.99
ANN (second model): MSE ≈ 0.006, R² ≈ 0.9996
The second ANN model outperformed others, demonstrating highly accurate predictions of future lessons.

## Limitations

Data Sparsity: Certain lesson categories had fewer records, potentially limiting the model's ability to generalize across all categories.
Assumptions about Lesson Ceilings: The group-specific ceiling for lessons was calculated based on the 90th percentile within age groups. This may not always reflect individual progression trends and could cause under- or over-predictions in some cases.
Feature Availability: The model assumes that future lesson patterns will continue similarly to historical data, but it does not account for external factors (e.g., new policies, changes in lesson structure).

## Trade-offs

Model Complexity vs. Interpretability: While ANN provided the best performance, its complexity makes it less interpretable than simpler models like Random Forest or Linear Regression.
Overfitting vs. Generalization: The ANN models were carefully tuned to prevent overfitting. However, increasing model complexity comes with a higher risk of overfitting if not cross-validated properly.
Performance on Small Data: Logistic and Linear Regression models provided reasonable accuracy with smaller data, but they may not capture complex relationships as effectively as more advanced models like Random Forest or XGBoost. 
