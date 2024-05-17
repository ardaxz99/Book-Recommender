# Book-Recommender


## Main Objective

**Show how we can explore the subject of a book recommender system.**

Showing creativity and creating a "story" or purpose for each step taken is a plus.
Display the robustness, usefulness of our system. 

Our system goal is to : *(to complete)*
- Predict books according to books read by a user (precise if we want to avoid books he dislikes or focus on books he would love)
- Recommend books according to books similarity ? 
- Predicting ratings for a given book according to a user ?
- Compare cold start user to regular user of the rating website (or our imaginary recommender website)

## Objectives 

**Graph Analysis** : 
*Using the class material to describe our graph data.* 
As our graph is quite large (~54k user, 10k books, millions of edges),it may be needed to do some pre-processing such as reducing the number of edges to 100k by applying a co-similarity threshold. Graph metrics should be interpretated in order to describe the data & if possible justify our training choices / methods.


**Comparing different recommender systems** :

- By changing **methods / parameters / feature vectors**

    **Baseline Methods**
    1. Content filtering based approach
    2. User based collaborative filtering
    3. Item based collaborative filtering ? 
    4. KNN ? 
    5. Neural collaborative filtering

    **Data-Augmentation**

    Use of LLMs on Title / Authors -> wordvec embedding -> add to feature vector

    **Main method : GNNs**
    1. GraphSage (check Stellar Graph)
    2. GAN 
    3. CONV

    
- By using **metrics** : 
    1. ndcg, 
    2. precision

    Check paper : [https://arxiv.org/pdf/2007.13287] -> particurlarly the cost function ? 



- By different **testing methods** : 
    1. "I assume no new users; but users will only see 60/70% random items to build users features".
    2. "New Cold start users : users with only 1-10 random ratings". 
    3. "New cold start users : features build on only good ratings".
    4. "New cold start users : features build on only bad ratings". 


**Terms to check :** 
Cold start user

Importance Sampling 

*Last idea evoked* :  "Build the graph on the k means matrix ? then use wordvec ?"


### To dos : 
- [] Testings methods
- [] Graph analysis
- [] GNN