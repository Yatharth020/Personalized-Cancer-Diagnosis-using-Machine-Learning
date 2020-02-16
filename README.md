# Personalized-Cancer-Diagnosis

<img src = https://www.healtheuropa.eu/wp-content/uploads/2019/06/4X-image-768x432.jpg height = '400' width ='800'>

<h1>1. Business Problem</h1>
<p>Main objective of this project is to distinguishing the mutations that contribute to tumor growth (drivers) from the neutral mutations. Currently this interpretation of genetic mutations is being done manually. This is a very time-consuming task where a clinical pathologist has to manually review and classify every single genetic mutation based on evidence from text-based clinical literature. so designed a machine learning model that classifies given genetic variations/mutations based on evidence from text-based clinical literature. Got data from Kaggle which was updated by Memorial Sloan Kettering Cancer Centre. Data having some Gene, gene variations and some medical literature text related to gene variations.</p>

<h6> Problem statement : </h6>
<p> Classify the given genetic variations/mutations based on evidence from text-based clinical literature. </p>

<h2>1.3. Real-world/Business objectives and constraints.</h2>
* No low-latency requirement.

* Interpretability is important.

* Errors can be very costly.

* Probability of a data-point belonging to each class is needed.

# Methodology


- Clearly defining the business objective and deciding the right metric for the project is half work done,so we clearly laid out the norms of given problem and how to formulate a machine learning problem from it.


- <font color = 'red'>Univariate analysis and Baseline modelling  is performed on each of the three features:
    
    - <font color = 'black'> missing values are checked in the dataset and text preprocessing is performed on the text data.
    - Dominant classes are checked in the dataset for understanding the class imbalance.
    - We have used Tfidf Vectorization with trigrams,limitting to top 10000 features on the text data.
    - Logistic regression is used as our baseline model to see how well as individual features,are they able to predict the classes.
    - Stability of the feature is checked by understanding the distribution of training cross validation and test data.
    

- <font color = 'blue'>__Featurization of data__:
    - <font color = 'black'> We performed featurization of data using two approaches:
        - One hot Encoding: Countvectorizer and TfidefVectorizer are used for one hot encoding.Features of this featurization were used to train models which perform better with high dimensional data
        - Response Coding : we also performed response coding where probability values of a gene,variation or word
            belonging to a particular class is used as features.Then features were used to train models which perfoerm better on low dimensional data and 
    
    
- <font color = 'green' > __Modelling__:
    - <font color = 'black'> We perfomed Modelling on data using following Algorithms:
        - Naive Bayes : trained using one hot Coding features
        - Logistic Regression : trained using one hot coding features(we also trained LR model using features generated from bag of words featurization with bigrmas and uni grams)
        - KNN : trained using response coding features
        - Linear SVM : trained using one hot coding features
        - Random Forest : trained using both reponse coding and one hot coding
    
    
 
- <font color = 'violet'> __Stacking and Maximum voting Classifier__ :
    - <font color = 'black'>Finally we stacked logistic regression,linear SVM and MultiNomial Naive Bayes were used to build a stacked classifier
    and Voting Classifier was used to give the final output.
    
    
    
    
#### The alternate Feature engineering part

- Using the CountVectorizer with uni grams and bi grams for text,variation and gene data and impleneting a logistic regression model with balanced weights.

- Using TfidfVectorizer for all three of the features.limitting ourseleves to top 10000 features of the text and using uni,bi,tri and four grams along with logistic regression model which has class weights balanced
    
### Note : The most important part was to understand the model interpretability and metric chose and avoiding it to become a black box along with keeping a tab on data leakage for response coding part.
            
## Results 
<img src = https://github.com/yatscool007/Personalized-Cancer-Diagnosis/blob/master/New%20folder/Capture1.PNG>
<img src = https://github.com/yatscool007/Personalized-Cancer-Diagnosis/blob/master/New%20folder/Capture2.PNG>
<img src = https://github.com/yatscool007/Personalized-Cancer-Diagnosis/blob/master/New%20folder/Capture3.PNG>
<img src = https://github.com/yatscool007/Personalized-Cancer-Diagnosis/blob/master/New%20folder/Capture4.PNG>
<img src = https://github.com/yatscool007/Personalized-Cancer-Diagnosis/blob/master/New%20folder/Capture5.PNG>

### We find that though Logistic Regression with class balanced gives the least log loss on test data - 0.933 and cross validation loss - 0.976 and percentage of missclassified points are also aroud 30.5 percent which is reasonably good which we achieved using TFIDF vectorization with top 10000 features and ngram_range = (1,4).
