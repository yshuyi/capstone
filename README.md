# Capstone: NLP analysis of Sephora’s Reddit
by Yuan Shuyi

# Problem Statement

The global beauty industry is worth $511 billion. In 2019, Sephora USA earnings were $5.9b. 
In April 2020, at the peak of covid-lockdowns, Sephora, saw its foot traffic plunge 96.9%. 

Getting consumer feedback is one way of improving the bottom line. 
We turn to Reddit, where anonymous posting and specific communities make Reddit one of the best social media apps for researching and following your audience. 
Let’s carry out social listening on the chatter on Reddit’s Sephora 40.2k strong subreddit community created Aug 5, 201. After data extraction, cleaning and preprocessing, we carry out topic modelling and multi-label classification to find out topics the Sephora redditors focused on, before and after the onset of the pandemic. And sentiment analysis of those topics. 

# Data 

Data extracted via Pushshift.io Reddit API from [Sephora's Subreddit](https://www.reddit.com/r/Sephora/). All submissions and comments from 30 Apr 2014 - 28 Feb 2022 were scrapped. Total of 211,800 posts scrapped, of which there was 14,847 submissions and 196,953 comments.

# Data Dictionary
Description from [The Pushshift Reddit Dataset](https://arxiv.org/pdf/2001.08435v1.pdf)
|Columns|Type|Dataset|Description|
|---|---|---|---|
|**id**|*object*|sep_sub|The submission’s identifier, e.g., “5lcgjh”| 
|**created_utc**|*integer*|sep_sub|UNIX timestamp referring to the time of the submission’s creation, e.g.,1483228803|
|**num_comments**|*integer*|sep_sub|The number of comments associated with this submission, e.g., 7| 
|**link_flair_text**|*object*|sep_sub|The text of the link’s flair. This field is specific to subreddit. It is like a subcategory preset by admins.|
|**score**|*integer*|sep_sub|The score that the submission has accumulated. The score is the number of upvotes minus the number of downvotes. E.g., 5| 
|**title**|*object*|sep_sub|The title that is associated with the submission, e.g., “What did you think of the VIP Rouge benefits?”| 
|**selftext**|*object*|sep_sub|The text that is associated with the submission|
|**author**|*object*|sep_cmt|clustering of traps though DBScan and KNeighborsClassifier |
|**parent_id**|*object*|sep_cmt|Identifier of the parent of this comment, might be the identifier of the submission if it is top-level comment or the identifier of another comment, e.g., “t1 dbu5bpp”| 
|**body**|*object*|sep_cmt|The comment’s text, e.g., “This is an example comment”| 
