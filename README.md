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

# Summary of our findings

1. When comparing the top 20 words before and after covid-onset, the words 'store','point','sample','rewards','rouge' have completely fallen off the top 20 after covid onset, indicating that redditors have much less to say about their in-store shopping experiences and their VVIP Sephora Rouge membership and benefits.  

2. By using Latent Dirichlet Allocation (LDA) to perform topic modelling, there are twelve topics that we can manually label. They are 'purchases', 'skincare', 'fragrance', 'online order issues', 'shipping issues', 'makeup-lipwear', 'customer experience', 'makeup-natural', 'customer rewards', 'haircare', 'appreciation', 'makeup-longwear'. To reinforce the earlier findings, 'customer rewards' and 'customer experience' make up a smaller percentage of the topics after covid onset. 'Fragrance', 'makeup-natural' topics have an increase after covid onset.

3. At times, the reddit posts are about more than one topic. Eg: "I want to use my Rouge points on a perfume sample, but the promo code is not working." covers the topics of customer rewards, fragrance and online order issues. By feeding in our earlier twelve topics to zero-shot classification, we get a richer idea of the topics being discussed. On a subset of popular submissions, and threshold value of 85%, zero-shot returned 6,196 labels for 3,764 posts. 

4. Using the bertweet base sentiment analysis, the topics were scored as positive, neutral and negative. Although the sentiments about the topics before and after covid did not change much, there is significant amount of negative sentiments about 'online order issues' and 'shipping issues'. 

# Recommendations

1. Marketing team to target Rouge shoppers, or former Rouge shoppers and promote Shop-instore events
2. Service recovery with online order or delivery issues and monitoring of ‘humour’ category for product or services fails
3. Future work of identifying brands and product names trending over the SS/AW seasons
