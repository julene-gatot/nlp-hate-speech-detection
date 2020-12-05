## Step 0: Preparation
- Reading the research paper first to get some context about the dataset and problem
   - Data gathering method
   - Data annotation
   - Data preparation/preprocessing
   - What features were introduced
   - Model building and model performance
- Broader picture of NLP before narrowing it down to NLP on Tweets 
   - Focus is on how Tweets are handled
   - Preprocessing step
   - What were important features of Tweets to take note of
- Tying it back to the business problem


## Step 1: Understanding the problem through EDA
- Is the data balance
  - Research paper did not balance it to reflect a more realistic dataset
- Exploring hashtags and usernames 
   - Allows me to better understand the dataset I’m working with
   - What is the distribution of words (like hashtags, etc) in general and in the different classes

## Step 2: Preprocessing
- Cleaning the tweets and tokenizing it
- Lemmatizing
- Removing stopwords, excluding “not”
   - Inspired by research paper
- Looking at clean tweets
   - Blanks
   - Looking at the top frequency of tokens for each class
    - Non-statistical way of looking at which words/tokens are important for each class
    - Just based on the assumption that the higher frequency of tokens give the context of the tweet

## Step 3: Model Building
### Naive Bayes
- Baseline model
- To see how the model would perform in general
- A standard for the subsequent models
- Tried with tf-idf 
  - Did not work well because I think it isn’t compatible with multiple label classification and tf-idf weighted inputs

### Logistic Regression
- Gridsearch to find the best hyperparameters
   - Char
   - (1, 4) n-gram
   - 0.25 max document frequency
    - When building the vocabulary ignore terms that have a document frequency strictly higher than the given threshold (corpus-specific stop words)
    - Tune this because I want to ignore certain words (based on later evaluation)
- Feature importance
- Tf-idf vectorizer and their weights

#### Removing Blank Tweets
- Similar performance

#### Including the stopwords
- Remove the stopwords
- Weights for feature importance
- They are just noise

## Step 4: Testing on Test Set and its Results
- The class for sexism is concerningly low
  - Research paper didn’t really bring this up, they just presented the overall F1 score based on the different features they later included
- False Negative
  - Names involved
  - Each name do not really provide a specific meaning but rather give it context
- False positive
  - On the other hand, the model is picking up the words but interpreted it as sexist

### Concluding thoughts
-  Harder to identify for sexism
  - Need context (mkr for example) 
  - More nuance cleaning → importance of preprocessing step
