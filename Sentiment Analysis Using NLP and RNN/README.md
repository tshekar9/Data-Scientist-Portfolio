## Sentiment Analysis of Customer Review Data Using NLP and Neural Networks

![TensorFlow](https://img.shields.io/badge/TensorFlow-%23FF6F00.svg?style=for-the-badge&logo=TensorFlow&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-%23D00000.svg?style=for-the-badge&logo=Keras&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)

#### Tejaswini Shekar

### Goal of the Analysis
The primary goal of the analysis was to assess customer reviews for positive and negative sentiments using neural networks and natural language processing (NLP). 
By analyzing these sentiments, companies can receive actionable insights that inform decision-making.
The process involves cleaning and preprocessing the review data, followed by classification of the reviews using neural network models (RNN). 
The model identifies whether a review is positive or negative and the insights gained from the analysis can then be used to recommend actions for improvement. 

### Prescribed Network
Neural networks are a series of algorithms that aim to recognize relationships in data through a process mirroring the working of the human brain. 
Natural language processing involves using computer technology to manipulate human language (eg. email filters, search engines).
In this project, an RNN (recurrent neural network) will be used to analyze customer review data from three websites and identify positive and negative sentiments in them.

RNN was chosen for this analysis because it works well with sequential data. 
Text classification tasks such as sentiment analysis have sequential/temporal data. 
This means that the data is present in a sequence one after the other, like words in a sentence. Therefore using an RNN would be ideal for this analysis.

### Categories of Sentiment
The reviews will be categorised into two groups; 1 (positive sentiment) or 0 (negative sentiment).
The activation function for the final output layer is the sigmoid function. This activation function
provides an output between zero and one, and is commonly used for binary classification problems.
Since the sentiment analysis requires classification of the data into two categories; either positive or negative, this function is appropriate.

### Exploratory Data Analysis

<img width="1384" height="1034" alt="image" src="https://github.com/user-attachments/assets/e9a4e232-98ab-4f61-9b7e-c48930401a43" />

<img width="1502" height="922" alt="image" src="https://github.com/user-attachments/assets/7b668bd4-c4ed-4076-8505-78440ec38785" />

### Data Cleaning/Preprocessing
a. Check for null values.
b. Lowercase all the reviews to remove redundancies in lowercase/uppercase letters.
c. Irregular characters: Find the initial character count of the data. Remove punctuation, emojis/
irregular characters and recheck the character count (27).
d. Tokenize, remove stop words from the reviews and lemmetize the reviews:
These three steps were done together by defining a function with three parts and passing the dataset
into it.
e. Determine the final vocabulary size of the data after the previous data cleaning steps. This is
required to determine embedding length and build the neural network.
f. Vectorize the reviews. Vectorization is the process of converting text data into numerical data so
that it can be used by machine learning algorithms.
g. Check the minimum, maximum and median lengths of the vectorized reviews.
h. Pad the reviews to the maximum sequence length (44) as determined in the previous step. This
ensures that each review/input to the neural network is the same size and no review data is lost.

#### Split Data into Training and Test Sets
Split the processed data into training and testing sets using train_test_split from sklearn with an
80%(train)/ 20%(test) split as per industry standards.
The size of the validation set is 20% and this will be specified when building the neural network
with the argument "validation_split=0.2".


### Functionality of the Model

This neural network functions as a binary classifer for sentiment analysis of customer reviews. It can be used to categorise customer feedback as either positive (1) or negative(0).
The input layer of the network is an embedding layer that takes sequenced text as input and feeds it forward to the first hidden layer. The two hidden layers that come next perform computations on the data. 
They have 100 and 50 nodes respectively with "relu" activation functions. The nodes apply weights to the inputs and the activation functions introduce non-linearity so that the network can perform more complex calculations. The next layer is a pooling layer that reduces the dimensions of the input data. It computes the average output of each feature map of the preceeding layer and reduces its dimensions to make the model ready for the last classification layer.
The last layer is the output layer with only one node. It has a sigmoid activation function that provides an output probability between 0 and 1. This determines which category the review is most likely to belong to.
In this way, the neural network can take sequenced customer review data and categorise it as positive or negative.

### Model Architecture

#### Activation Functions:
Activation functions transform the output from one layer to another.
ReLU (Rectified Linear Unit) was selected as the activation function for the hidden layers because
it is computationally efficient and avoids the vanishing gradient problem.
The sigmoid activation function was selected for the output layer. It was selected because it
provides an output value between 0 and 1 which works well with binary classification problems
where the output is interpreted as a probability.

#### Number of Nodes Per Layer:
The number of nodes for the hidden layers was chosen arbitrarily based on the size of the available
training data and the nature of the classification problem. The first hidden layer has 100 nodes and
the second hdden layer has 50 nodes.
The output layer has only one node since this is a binary classification problem requiring an output
of either 0 or 1.

#### Loss Function:
The loss function used in the model is binary cross entropy since this is a classification analysis
with binary categories of 0 and 1.

#### Optimizer:
The optimizer used for this analysis is "adam" since it is easy to implement, computationally
efficient and combines the best aspects of other optimziers. It iteratively adjusts weights and adapts
the learning rate thus effectively reducing overfitting.

#### Stopping Criteria:
Early stopping criteria was used to prevent the model from overfitting and improving the
generalization of the final model. The stopping criteria used for this analysis was the
EarlyStopping() method from tensorflow.keras.callbacks with patience=2. This means that model
training will stop if validation loss fails to improve for two continuous epochs.From the training
process, it is clear that validation loss decreases from epoch 1 to 2 and 2 to 3. However, the
validation loss increases from epoch 3 to 4 and again from epoch 4 to 5. This causes the model to
stop training early since the early stopping criteria has been met (even though the number of epochs
initially provided was 20). If the model continues training beyond this point, it would only lead to
worsening results.

### Results and Recommendations

Accuracy is the number of correct predictions divided by the total number of predicitons, expressed
as a percentage. A higher predictive accuracy indicates a better model. For this model:

Training Accuracy: **93.58%**
Test Accuracy: **80.67%**

The testing accuracy is high indicating a good model. Also, the difference between the two
accuracies is less than 15%. This shows that the model is good as per indutry standards since the
difference between training and testing accuracies should be between 5%-15%.

I was able to answer the initial research question as to whether it is possible to build a neural network that is able to accurately classify a review as positive or negative. 
Since the testing accuracy of the model was above 75%, it is clear that it is possible to build such a model.

This neural network has a high enough test accuracy that it can be used in a real-world environment.
Some of the possible applications for this model include customer satisfaction analysis and evaluating feedback on new product launches.
I would also recommend collecting more customer review data for model training to improve its predictive accuracy even further.
