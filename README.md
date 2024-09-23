# Swimclub ML Data Analysis


## NON-TECHNICAL EXPLANATION OF YOUR PROJECT
This project explores advanced machine learning techniques to predict how many future swim lessons a club member is likely to take based on historical class participation. Using models like Linear Regression, Random Forest, XGBoost, and a finely-tuned Artificial Neural Network (ANN), the project forecasts swim lesson attendance. The analysis of member data, including class sequences and patterns, helps the swim club plan resources more efficiently and tailor personalized services to members based on their predicted future participation.

## DATA
The data was provided by a swim club covering the last five years of operations, including class participation details for each member, progression through levels, age at key stages, and whether they are current or former members. The dataset allows the analysis of how past behavior influences future lesson participation, focusing on class sequencing—how members progress over time and the number of lessons completed at each stage. This approach improves the prediction of future behavior based on historical progression patterns, rather than just using static features.

## MODEL 
Data Preparation: The dataset was split into leavers (former members) and current members. Class sequencing features were created to track progression through the swim levels over time, focusing on how the number of lessons changes throughout membership.

Feature Engineering: Various features were engineered, such as deviations from the median number of lessons (Variance to Median - VTM) and class-level sequencing to capture patterns of attendance. This allowed for better generalization and pattern recognition in the predictive models.

Training and Testing Split: For former members, the data was split 70/30 for training and testing, respectively. For current members (where the total number of future lessons is unknown), only the completed lesson sequence was used for training models.

Model Selection: Different models, including Random Forest, XGBoost, and ANN, were trained to predict future lesson numbers. Models were compared based on their performance when handling cases with partial information (i.e., current members with incomplete class sequences).

Evaluation Metrics: The models were evaluated using Mean Squared Error (MSE) and R-squared (R²). Comparisons were made across models with fewer classes known to simulate limited information scenarios.

## HYPERPARAMETER OPTIMSATION
Throughout the development of the predictive models, various hyperparameters were tuned to improve accuracy and generalization. The focus was on handling limited data (when only part of a member's total lesson sequence is known), ensuring models could accurately predict the remainder of the sequence.

Random Forest:
n_estimators: Set at 100 for an optimal balance between performance and complexity.
max_depth: Tuned to prevent overfitting, yielding the best results with a moderate depth.
XGBoost:
n_estimators: Set to 100.
learning_rate: A learning rate of 0.1 was chosen to ensure steady, effective learning.
max_depth: Tuned to prevent overfitting, allowing the model to capture sufficient patterns without adding noise.
Artificial Neural Network (ANN):
Layers and Neurons: A multi-layer ANN was developed with 3 hidden layers, using 128, 64, and 32 neurons. This allowed the model to capture complex, non-linear relationships.
Activation Functions: A combination of ReLU and tanh was used to improve performance in deeper layers.
Batch Size and Epochs: The batch size was set to 64, and 200 epochs were used for training, ensuring the model converged effectively.
Optimizer: Adam optimizer was used with a learning rate of 0.001 for its balance of speed and accuracy.
Manual hyperparameter tuning was used, along with cross-validation to ensure robustness. Special attention was paid to overfitting through regular monitoring of training and validation loss.

## RESULTS
The project tested and evaluated multiple models, including Random Forest, XGBoost, Linear Regression, and Artificial Neural Networks (ANN), across scenarios where only partial data was available (for current members). The results showed significant differences in performance depending on the model and the amount of known data.

Summary of Results for Limited Data:
Classes Used: 8: The ANN Tuned model performed best with a Mean Squared Error (MSE) of 212.28 and R² of 0.92, showing that it captured progression patterns well even with incomplete class data.

Classes Used: 5: The ANN Tuned model also performed best in this scenario, with an MSE of 702.24 and R² of 0.74. This demonstrated its ability to handle more challenging, limited data scenarios better than Random Forest and XGBoost.

Classes Used: 2: In very limited data scenarios, XGBoost slightly outperformed the ANN with an MSE of 2239.14 and R² of 0.16, showing its robustness when handling minimal information.

Key Learnings:
Class Sequencing: The introduction of class sequencing data improved model predictions by capturing how members typically progress through swim levels.
Handling Limited Data: ANN models were generally better at predicting with partial data (8 or 5 known classes), while XGBoost slightly outperformed ANN when only 2 classes were known.
Practical Implications: Swim clubs can use these models to predict future attendance, enabling better resource planning, scheduling, and personalized member retention strategies.



