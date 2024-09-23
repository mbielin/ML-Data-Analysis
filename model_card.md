# Model Card

See the [example Google model cards](https://modelcards.withgoogle.com/model-reports) for inspiration. 

## Model Description

Input: The models were trained on historical data from a swim club, covering the last five years of operations across multiple locations. The data included key information such as member demographics (age, membership status), lesson participation history (including PreSchool and Academy lessons), and discounts applied. Important input features included:

Age_joined
Age_at_last_lesson (for leavers only)
TOTAL QUANTITY OF LESSONS
Variance to Median (VTM) for PreSchool and Academy lessons
Various discount columns (e.g., SIBLING DISCOUNT APPLIED, PROMOTIONS APPLIED)
Output: The models predict the number of future swimming lessons a member is likely to take. Some models, such as Logistic Regression, predict a binary outcome for whether a member will take more than a specific number of future lessons.

Model Architecture: We tested and compared the following models:

Random Forest Regression: A tree-based ensemble method with 100 estimators.
XGBoost Regression: A gradient-boosting method optimized with a learning rate of 0.1 and a max depth of 5.
Linear Regression: A simple approach modeling the relationship between features and future lessons.
Logistic Regression: Used for binary classification of future lessons.
Artificial Neural Networks (ANNs):
First version: Two hidden layers with 64 and 32 neurons using ReLU activation.
Second version: Deeper architecture with 128, 64, and 32 neurons using a combination of tanh and ReLU activations.

## Performance

Evaluation Metrics:

Mean Squared Error (MSE): Measures how close predictions are to actual future lessons.
R-squared (R²): Explains the variance captured by the model.
Performance Summary:

Random Forest Regression: MSE ≈ 0.33, R² ≈ 0.98
XGBoost Regression: MSE ≈ 0.30, R² ≈ 0.99
ANN (first model): MSE ≈ 0.10, R² ≈ 0.99
ANN (second model): MSE ≈ 0.006, R² ≈ 0.9996
The second ANN model consistently outperformed other models, demonstrating highly accurate predictions of future lesson

## Limitations

Data Sparsity: Some lesson categories had fewer records, potentially limiting generalization across all categories.
Feature Availability: The model assumes that future lesson patterns follow historical trends and does not account for new external factors (e.g., policy changes, new lesson structures).
Assumptions About Patterns: No ceiling was applied to limit total lessons based on percentiles in the final model iterations, meaning the predictions are less constrained by historical upper limits and could risk over- or under-predicting in some cases.

## Trade-offs

Model Complexity vs. Interpretability: While the ANN models offered the best performance, their complexity makes them harder to interpret than simpler models like Random Forest or Linear Regression.
Overfitting vs. Generalization: The ANN models were carefully tuned to avoid overfitting. However, as model complexity increases, so does the risk of overfitting if not handled correctly.
Performance on Smaller Data: Simpler models like Logistic and Linear Regression worked well with smaller data but lacked the complexity needed to capture deeper relationships in the data compared to models like XGBoost or ANN.
 
