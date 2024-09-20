# An Exploration into a variety of models to predict future swimclub lessons 


## NON-TECHNICAL EXPLANATION OF YOUR PROJECT
This project uses ten machine learning models to predict how many future lessons a swim class member is likely to take. Starting with Random Forest Regression, it explores different algorithms such as Linear Regression, Logistic Regression, and advanced models like XGBoost and Artificial Neural Networks (ANNs). Each model was trained on historical data of swim lessons to forecast future attendance. The second ANN, our most complex model, demonstrated the highest accuracy due to its sophisticated architecture, yielding precise predictions. By analysing member data, these models help the swim club plan ahead and personalize their services effectively.

## DATA
The data used in this project was provided by a swim club company, covering the last five years of operations across various locations. The dataset includes detailed information on swim class participants, including the number of lessons taken, age at different stages, class levels, and any discounts applied. Each row represents a swim club member and tracks their progression through the different lesson levels, along with their membership status (current or former). This rich dataset allows us to analyze trends and forecast how many future lessons members are likely to take based on their historical participation

## MODEL 
The primary goal of the project is to predict how many future swim lessons a club member might take. To achieve this, various machine learning models were implemented, starting with Random Forest Regression and including models such as Linear Regression, Logistic Regression, XGBoost, and Artificial Neural Networks (ANN).

Workflow summary:

Data Preparation: The dataset was split into two groups—members who left the club ("leavers") and those who are still active ("current members"). Features such as age, lessons taken, and discount information were prepared, and a variance-to-median (VTM) calculation was applied to analyze deviations from typical behavior.

Feature Engineering: Additional features were engineered, such as a 90th percentile ceiling on lessons to prevent overestimation of future lessons, and the creation of group-specific ceiling values based on age groups.

Training and Testing Split: The data for leavers was split into training and testing sets, with 70% used for training the models and 30% for evaluating their performance.

Model Selection: Different models were tested, including Random Forest, XGBoost, and ANN models. The models aimed to predict the number of future lessons based on the features mentioned. ANN models were further optimized with varying hyperparameters such as learning rates, number of layers, and neurons.

Scaling and Normalization: Feature scaling was applied to ensure consistent data representation, especially for models like ANN and XGBoost that are sensitive to the scale of the input features.

Evaluation: Each model was evaluated using metrics such as Mean Squared Error (MSE) and R-squared (R²) to gauge their prediction accuracy. The models were then used to forecast future lessons for current members.

## HYPERPARAMETER OPTIMSATION
During the process of developing predictive models, hyperparameters were tuned to optimize the performance of models like Random Forest, XGBoost, and Artificial Neural Networks (ANN). Hyperparameters were carefully selected to improve model accuracy and prevent overfitting.

Random Forest Regression:

n_estimators: This defines the number of trees in the forest. Initially, a default of 100 trees was chosen. More trees can increase accuracy but also computational complexity. After evaluation, the default value of 100 worked well.
max_depth: This limits how deep the trees can grow. Although the default was tested, restricting the depth prevents overfitting. This was optimized to achieve a balance between model complexity and performance.
random_state: Set to 42 to ensure reproducibility of results.
XGBoost:

n_estimators: The number of boosting rounds or trees. A default of 100 estimators was used to balance performance and computation time. After initial evaluation, no significant improvement was seen by increasing beyond 100.
learning_rate: Controls the contribution of each tree in boosting. A learning rate of 0.1 was selected, which allows for more stable training while still achieving good performance.
max_depth: Set to 5, limiting the depth of each tree to prevent overfitting. This depth was chosen based on model evaluation, as deeper trees did not significantly improve results but increased complexity.
Artificial Neural Networks (ANN):

Number of Layers and Neurons: Two ANN models were tested. The first model had 2 hidden layers with 64 and 32 neurons, and the second ANN had 3 hidden layers with 128, 64, and 32 neurons, using ReLU and tanh activations. This setup was optimized based on performance through trial and error, where increasing the number of neurons and layers helped in capturing more complex patterns in the data.
Activation Functions: The models used a combination of ReLU for faster convergence and tanh for non-linearity in deeper layers. The inclusion of tanh was tested to capture more complex relationships in the data.
Batch Size and Epochs: The batch size was increased to 64 and the number of epochs was increased to 200 in the second ANN model to allow the model to converge more effectively.
Optimizer: Adam optimizer was used with a learning rate of 0.001. Adam was chosen for its efficient handling of sparse gradients and fast convergence. The learning rate was optimized to avoid overshooting the minimum loss.
Optimization Process:
The hyperparameters were tuned using manual trial and error, adjusting the values incrementally based on the performance metrics (Mean Squared Error and R²). Cross-validation was employed for Random Forest and XGBoost to evaluate the models' generalization capability. For ANN, training and validation losses were monitored to prevent overfitting by adjusting the number of epochs and learning rate.

## RESULTS
After developing and testing multiple machine learning models (Random Forest, XGBoost, Linear Regression, Logistic Regression, and Artificial Neural Networks), the results demonstrated strong predictive capabilities in forecasting future swimming lessons for club members. Key performance metrics, such as Mean Squared Error (MSE) and R-squared (R²), were used to assess model accuracy.

Random Forest Regression: Delivered reliable results with an R² score of approximately 0.98, making it one of the best models for predicting the number of future lessons members would take.
XGBoost: Achieved similar performance, with an MSE close to 0.3 and R² around 0.99, showing robust generalization and efficiency with boosting techniques.
Artificial Neural Networks (ANN): The second ANN model with enhanced layers and neurons provided the best result, with an R² as high as 0.9996 and a significantly low MSE (~0.006). This demonstrated the model's ability to capture complex patterns in the data when fine-tuned.
Key Learnings:
Data Representation: The inclusion of Variance to Median (VTM) columns for each lesson, representing deviations from the median, enhanced the model's ability to interpret historical lessons and predict future ones accurately.

Age Groups and Lesson Ceilings: Introducing age groups and group-specific ceilings based on the 90th percentile of lessons provided a more realistic boundary for future lesson predictions. This prevented overestimation and aligned predictions more closely with historical trends.

ANN Model Performance: The ANN, with its deeper architecture and non-linear activation functions, excelled in identifying intricate relationships in the data that simpler models like linear regression could not capture. It reinforced the idea that complex models can outperform simpler ones when enough data and computational power are available.

Overfitting Prevention: Cross-validation and careful selection of hyperparameters helped prevent overfitting, ensuring that the models would generalize well to unseen data.

Practical Implications:
The results suggest that swim clubs can confidently use these models to predict future lesson enrollment, allowing better resource allocation, scheduling, and personalized engagement with members. Furthermore, the models can provide insights into member retention strategies by identifying those likely to continue based on their past engagement patterns.



