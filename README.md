# Exploring-Stock-Price-Prediction-with-Deep-Learning
This report explores the application of deep learning for stock price prediction. It investigates the effectiveness of GRU neural networks in analyzing historical data to forecast closing prices for multiple companies.
#ABSTRACT
##Modeling Approach
This document details the application of deep learning, using TensorFlow and Keras, to predict closing stock prices for six companies over the next 96 days. Here's a breakdown of our modeling approach:

Data Preparation: We gathered historical stock price data and preprocessed it by handling missing values, normalizing the data, and creating relevant features.

Model Architecture Selection: A sequential model architecture was chosen and configured with GRU layers to capture temporal dependencies within the data.

Model Compilation: The model was compiled using mean squared error (MSE) as the loss function and the Adam optimizer for effective training.

Training: The model was trained on the preprocessed data, with hyperparameters fine-tuned as needed.

Evaluation: The model's performance was evaluated using metrics like mean absolute error (MAE), mean squared error (MSE), and visual inspection of predicted versus actual closing prices.

##Model Architecture
This architecture consists of three GRU layers, each with 32 units. The first two layers return sequences. A dropout layer with a 20% dropout rate is incorporated to prevent overfitting. Finally, a single-unit Dense layer serves as the output layer. The model is compiled using mean squared error loss and the Adam optimizer.

Data Preparation and Preprocessing - Univariate Strategy
Our strategy focused on a univariate time series approach specifically designed for predicting closing prices. While we considered multivariate methods, the univariate approach consistently delivered superior results, particularly in terms of prediction accuracy.

Normalization Using MinMaxScaler
We employed MinMaxScaler to normalize closing prices within a range of 0 to 1. This technique ensured numerical stability and facilitated convergence during training. By mitigating the influence of outliers and addressing inconsistencies in scales across various stocks, it significantly enhanced the robustness of our models.

##Predictions
Sliding Window Method: During training, the model was primed with a look-back window of 200 timesteps. This means it analyzed 200 consecutive historical data points to forecast the subsequent day's closing price. For the test dataset prediction phase, we adopted a recursive approach. Initially, we utilized the latest 200 values from the training set to predict the first value of the test set. Subsequently, for each prediction, we used the most recent 199 values from the training set along with the previously predicted value. This ensemble of 200 timesteps was then iteratively fed into the model to generate successive predictions.

##Results
Peak Performance: After multiple refinement cycles, our model achieved its peak performance, yielding a Root Mean Square Error (RMSE) of 111.8159 across 52% of the test dataset. This metric represents the average difference between actual and predicted closing prices.

Performance Fluctuations: It's important to note that our model exhibited fluctuations in performance across different segments of the test dataset. While it maintained an RMSE of 111.8159 on 52% of the test data, its efficacy declined to 345.5134 in other segments. Additionally, one of our initial models obtained an RMSE of 244.8535 on 52% of the dataset, but improved significantly to 110.819. This variability underscores the model's sensitivity to specific data subsets and the iterative nature of model refinement.

##Other Approaches
Here are the other models and approaches we explored:

Long Short-Term Memory (LSTM) Networks
Transformer Models
Linear Regression
