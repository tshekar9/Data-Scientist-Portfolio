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

I have chosen an RNN for this analysis because it works well with sequential data. 
Text classification tasks such as sentiment analysis have sequential/temporal data. 
This means that the data is present in a sequence one after the other, like words in a sentence. Therefore using an RNN would be ideal for this analysis.

### Functionality of the Model

This neural network functions as a binary classifer for sentiment analysis of customer reviews. It can be used to categorise customer feedback as either positive (1) or negative(0).
The input layer of the network is an embedding layer that takes sequenced text as input and feeds it forward to the first hidden layer. The two hidden layers that come next perform computations on the data. 
They have 100 and 50 nodes respectively with "relu" activation functions. The nodes apply weights to the inputs and the activation functions introduce non-linearity so that the network can perform more complex calculations. The next layer is a pooling layer that reduces the dimensions of the input data. It computes the average output of each feature map of the preceeding layer and reduces its dimensions to make the model ready for the last classification layer.
The last layer is the output layer with only one node. It has a sigmoid activation function that provides an output probability between 0 and 1. This determines which category the review is most likely to belong to.
In this way, the neural netowork can take sequenced customer review data and categorise it as positive or negative.

### Results and Recommendations

I was able to answer the initial research question as to whether it is possible to build a neural network that is able to accurately classify a review as positive or negative. 
Since the testing accuracy of the model was above 75%, it is clear that it is possible to build such a model.

This neural network has a high enough test accuracy that it can be used in a real-world environment.
Some of the possible applications for this model include customer satisfaction analysis and evaluating feedback on new product launches.
I would also recommend collecting more customer review data for model training to improve its predictive accuracy even further.
