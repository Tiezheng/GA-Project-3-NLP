

## Problem Statement 

International Basketball Federation (FIBA) is an association of national organizations which governs the sport of basketball worldwide. In recent years, the number of basketball fans worldwide had dwindled and many former basketball fans had switched to soccer. FIBA wants to identify the key words that can best capture the attention of its'fans so as to differentiate itself from soccer. This would facilitate FIBA's marketing effort on social medial to create short but impactful phrases. FIBA had approached reddit data science department for this project.     

Therefore, the goal of the project is to discover the key words that best differentiate basketball fans from soccer fans in reddit posts. 

Three classification models, Naive Bayes, Logistic Regression and K-Nearest Neighbors will be developed. 

The success of the model will be assessed based on its mean accuracy, precision and recall on unseen data. 

There are 69.6K Basketball fans and 2.3 million soccer fans respectively on reddit. These fans come from all over the world. The models that will be developed are capable of accurately classify the two subreddits. There are enough unique posts in each subreddit to identify key words to achieve our research goal. Therefore, the scope of the project is appropriate. 

This project is important to FIBA to reduce customer(fans) churn and to win back former fans. Otherwise, basketball fans worldwide will continue to dwindle. This has negatively affect major basketball leagues. Their ticket sales, membership and merchandise had experienced drastic drop. FIBA funding will be affected if fans continue to leave. 

The primary stakeholder is FIBA. FIBA can use the key words identified to develop a successful marketing campaign to increase fan base. The secondary stakeholder will be major basketball associations for example NBA and the teams in it. They would benefit in terms of ticket sales, membership sign up, pay per view and merchandise sales. 


## Executive Summary 

### Contents:
- [1. Importing the Libraries](#1.-Importing-the-Libraries)
- [2. Importing Datasets](#2.-Importing-Datasets)
- [3. Inspection of Dataset](#3.-Inspection-of-Training-and-Test-Dataset)
- [4. Data Cleaning](#4.-Data-Cleaning)
- [5. Pre-processing](#5.-Pre-processing)
- [6. Exploratory Data Analysis (EDA)](#6.-Exploratory-Data-Analysis-(EDA))
- [7. Create Feature Matrix and Target](#7.-Create-Feature-Matrix-and-Target)
- [8. Model Selection](#8.-Model-Selection)
- [9. Selected Model and Business Recommendations](#9.-Selected-Model-and-Business-Recommendations)
- [10. Future Steps](#10.-Future-Steps)

### Data Dictionary

There are two engineered features and they are text and text length

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**title**|*object*|df|The title of the post.| 
|**selftext**|*object*|df|The text in the post.|
|**upvote_ratio**|*float*|df|The ratio of total votes that are in support(up) of the post.|
|**ups**|*int*|df|Total number of support votes of the post.| 
|**score**|*int*|df|The difference between support votes and down votes of a post.|
|**num_comments**|*int*|df|Number of comments of a post|
|**subreddit**|*object*|df|Which subreddit did the post come from, either basketball or soccer.|
|**text**|*object*|df|The combine of title and selftext.|
|**text length**|*int*|df|The length of text.|


### Data Cleaning

1. All duplicated data were removed 
2. Null cells were replaced with empty spaces 
3. All text were converted to lower case
4. All non letters were removed
5. All HTML special entities removed
6. All hyperlinks removed
7. All punctuations removed
8. Words with 2 or fewer letters removed
9. Whitespace were removed
10. All emoji removed
11. Remove characters beyond Basic Multilingual Plane (BMP) of Unicode
12. All words were lemmatized 


### Justification for picking Logistic Regression TF-IDF & Interpretation of Model

1. TF-IDF penalize common words and give rare words more influence. This is relevant to our problem statement, basketball posts and soccer posts tends to use different terms. For example, basketball post might commonly use the word "NBA" because that is the most popular basketball association. On the other hand, soccer post might commonly find the word "EPL" or "Premier League" because that is a popular football league. Therefore, penalize common words and giving more influence to rare words would help us in our classification problem. 

2. Comparing the model scores of CountVectorizer and TfidfVectorizer, in all instances models under TfidfVectorizer scores better. 

3. Why Logistic Regression? Logistic Regression gives a high mean accuracy score for both training data (0.9895470383275261) and test data (0.9498607242339833). This means that the model generalises well and scores well on unseen data. It returns one of the highest test score amongst all models. It also scores much better than the baseline score.  

4. The model also has a high recall (i.e the percent of positive cases I catch) of 0.96 for basketball. It also has a high precision (i.e the percent of my predictions were correct) score of 0.95 for basketball. 
 
5. Logistic Regression allows me to interpret model coefficients as indicators of feature importance. 
    - For example, the presence of the word "basketball" increases by 1, the post is about 44 times as likely to be a basketball post. You might think that the presence of the word "basketball" in basketball post are very common. However, based on domin knowledge, it can also be interpreted as basketball fans likes to stay true to the game and not involve the sport in politics. For example, NBA icon Charles Barkley ones mentioned, fans dont like to see politics in the sport. (https://www.bet.com/news/sports/2020/07/14/charles-barkley-nba-social-justice.html)  
    - Similarly, the presence of the word "nba" increases by 1, the post is about 17.2 times as likely to be a basketball post. Based on domin knowledge, NBA is the most popular basketball league in the world. It has many famous basketball icons such as Michael Jordan and Kobe Bryant who have huge fan base all over the world. It is therefore logical for the word 'nba' to be ranked as the top few most impactful words. 
    - Based on reading the posts in reddit, basketball fans are also very interested in finding out how to improve their basketball skills. For example, there were many post that ask for tips to improve jumping abiltiy, shooting accuracy and game tactics. It is therefore, logical for words such as 'game', 'good', 'know', 'tip' and 'shoot' to be among the significant words. 
    - On the other hand, the presence of words such as "club", "goal", "penalty", "chelsea", 'loan" indicates that the post is most likely a soccer post instead of basketball post. 
    - The interpretation of coefficients allows us to make useful recommendations for our problem statement.  

6. Logistic Regression also has some limiations, for instance it assumes independence of independent Variables and the independent variables X1, . . . , Xm are linearly related to the logit of the probability. These are assumations however it may not always be the case. Nonetheless, for our problem statement, logistic regression is an useful model. 

### Conclusion & Recommendation

#### Search Engine Optimisation (SEO)
Based on our research through reddit post and our logistic model, keys words such as Basketball, NBA, Game, Good, Like, Know, Ball, Tip and Shoot are the words that best indicate a basketball post. This means that, basetball fans likes to use such words and would engage in discussions around such topics. Therefore, FIBA can include these words during their web improvement process to boost online presence.
    
#### Keep the Marketing Message Short and Sweet
Based on our research, basketball posts are generally shorter than football posts. This means that, basketball fans prefer short and concise text. Research result also shows that shorter texts tends to get more up votes compared to longer post. Social media platforms would be a good channel for FIBA's markeing effort. For example Twitter. Twitter only allows 140 texts per post, therefore its message is short and concise. Basketball fans might like such style.
    
#### Marketing Message Needs to be Meaningful
Research result shows that the number of comments has a moderate positive correlation with posts score and support votes(ups). This means that, basketball fans appreciates meaningful content and they are more willing to participate in discussions that interests them. Besides that, our result indicated that the number of comments in basketball posts are generally fewer than soccer posts. This means that the current basketball posts are not engaging and there are few fans participating in discussion.

FIBA can use the key words identified in our model to create meaningful discussion topics. For example, a discussion on NBA players playing style. Besides that, research findings also indicate that basketball fans are also interested in improving their own game. From the word cloud and logistic model, words such as know, tip, help, better and shoot kept coming up. This means that, basketball fans are seeking information that can help them improve their game. Therefore, FIBA's marketing campaign can include educational aspect in it. The presence of relevant key words would attract the attention of basketball fans and therefore trigger active discussion.

#### Avoid Aggressive Marketing Campaign
The strategy of aggressive marketing should be avoided. Aggressive marketing is kind of marketing campaign where one brand will expose the weakness of its rival brand. For example, Coca Cola attacking pepsi or Mercedes attacking BMW in their advertisement. FIBA's marketing campaign should only focus on Basketball and not involve other elements. Basketball fans likes to stay true to the game therefore the marketing campaign needs to be pure. 

#### Conclusion 
This project first started by scrapping unique posts from reddit, the data was inspected and cleaned for analysis. In exploratory data analysis (EDA), we compared the general behavioural and relationships (text length, votes, scores, ups) of basketball fans and soccer fans. We have also use word cloud to identify common words. Next, models were build to make predicitions on unseen data. Logistic regression was identified as the most appropriate model, its coefficients were interpreted (i.e. impact of key words interpreted). Meaningful recommendations were given based on EDA and model. Therefore, each individual step connects to the overall project.

Our research had successfully answered the original problem statement, which is to discover the key words that best differentiate basketball fans from soccer fans in reddit posts. We have also use these key words to derive marketing strategies. 

FIBA can use the recommendations above to better engage with its fans so as to reduce customer(fans) churn and to win back former fans. Otherwise, basketball fans worldwide will continue to dwindle. With a large active fan base, FIBA can more easily secure funding and sponsorship. Secondary stakeholders such as major basketball associations for example NBA and the teams in it. They would benefit in terms of ticket sales, membership sign up, pay per view and merchandise sales.


## Future Steps
- In the future, a larger dataset could be gathered. Currently, only around 900 unique posts were gathered for basketball and 800 posts for soccer. A larger dataset would be better for us to make inference of the population. 
- More models could be applied, for example models such as random forest and artificial neural network could be explored in the future. These are advanced models which might provide better predicitions. 
- Future research can combine both qualitative and quantitative methods. We are basically studying human behavioural, our data science research can be supported by interviews or focus groups. This would allow us to discover more meaning behind our findings. For example, we can invite basketfall fans to discuss about the keys words identified in our model. This would help us derive meaning from the fans perspective. 
- Our model is limited to the corpus of texts obtained from scrapping soccer and basketball reddit APIs. It would be better if the model can learn on its own, constantly update new text. This would allow the model to stay relevant longer. 
- Currently, our model only analyse basketball and soccer texts. In the future, the model can be expanded to include more sports. 