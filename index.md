***

# Abstract
Nowadays, anyone with a smartphone and an Internet connection can become a YouTuber. Many beginners dream of success on the platform, with videos acclaimed by millions of subscribers. However, reaching fame is not as easy as it seems: indeed, with how much the number of creators has grown in the past years, it has become increasingly difficult to make an impact. The difference between famous and unknown YouTubers may lie in more than the quality of their videos. Are there any metrics in famous YouTubers' most viral videos - title, length, category, upload date - that set them apart from the rest? Could these metrics be used to create a guide for YouTubers who are starting out?


***


![image](images\sebastian-pandelache-taPBy6XyMoQ-unsplash.jpg)



# Preprocessing - What data will we analyse?

To answer these questions, we will use a large dataset of YouTube channels and videos: YouNiverse. The dataset is divided into three main types of data: 
- Channel data, containing e. g. the date a channel registered on YouTube, its number of subscribers, etc.
- Video data, containing a video's title, its tags, its length and its number of views.
- Timeseries data, containing channels' weekly evolution (e. g. in terms of subscriber count) from 2015 to 2019.

{% include categories.html %}

We selected channels in the Entertainment category, which has the largest number of channels in the database.

Then, we calculated a "growth score", that is, an indicator of the channels' viral success. The score was calculated by dividing the channel's number of subscribers in the latest timeseries by the number of days the channel was active (date of the latest timeseries - date of the channel's registration). We kept the 15% of channels with the best growth score as our "buzzing" channels, and the 15% with the worst score as our "quiet" channels.


# The story of Ada - Chapter 1: My first video

*Hi,*

*My name is Ada, I heard you were doing research on how small YouTubers can become successful, so that's why I reached out.*

*So here's the whole story: I'm a uni student, I like to make small vlogs about my daily life and share them with my friends. Some time ago, they suggested I put them on YouTube, which I thought was an exciting idea! Can you imagine, so many people around the world seeing my videos! So I've been uploading my videos, but I've barely been getting any views... I'm so confused, what am I doing wrong? Vlogs are popular, plus I film with top-notch material and I work a lot on the editing too... Is there anything else which could help me grow my channel?*

*Thanks, Ada Westerlain*

![image](images\ada_part1_white.jpg)

# Evaluating relevant criteria for the success of a YouTube video

TODO: Describe the criteria analysis, as a response to Ada's question.

TODO IF POSSIBLE: Include the interactive tool for predicting a video's success based on title, length...


# The story of Ada - Chapter 2: The importance of the title

*Hi!*

*I've got good news: the videos I've posted since last time have been so successful! I made sure to follow your advice about the title and the tags, you know adding relevant words and capitalization and all that. I've even got more than 100 subscribers now! Oh and don't know if that helped, but I also changed the titles of my old videos - looking back, they were so bad hahaha*

*I still have some questions though... Sometimes there's a big difference in the number of views I get on each video. One time I vlogged about my classes at uni, and that video totally flopped! And even my most viewed videos never go over a few thousand views... Am I just not making videos about lame topics or what?*

*Thank you so much! Ada*

![image](images\ada_part2_white.jpg)

# Topical analysis - Which topics are successful for Entertainment channels on YouTube?

TODO: describe the topic analysis as a response to Ada's question.

# The story of Ada - Chapter 3: The buzz

TODO: Ada sends another message, she focused on more popular topics and her channel exploded

![image](images\ada_part3_white.jpg)

# Conclusion



{% include features_importance.html %}

{% include title_features_importance.html %}

{% include buzz_topics.html %}

{% include quiet_topics.html %}

{% include boxplot_mean_is_tags.html %}

{% include boxplot_mean_numwords.html %}

{% include boxplot_week_freq.html %}

![image](output/venn_lexical.png)

![image](output/relative_use_lexical.png)

![image](output/tags_quiet.png)

![image](output/tags_buzz.png)

![image](output/evolution_sub_ytb_lexical.png)

![image](output\wordcloud_tags_buzz.png)

![image](output\wordcloud_tags_quiet.png)


<script src="https://gist.github.com/zwierski/fe66b9662878b9f29f9a231190e215d2.js"></script>
