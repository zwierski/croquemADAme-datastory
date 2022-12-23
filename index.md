***

# Abstract
Nowadays, anyone with a smartphone and an Internet connection can become a YouTuber. Many beginners dream of success on the platform, with videos acclaimed by millions of subscribers. However, reaching fame is not as easy as it seems: indeed, with how much the number of creators has grown in the past years, it has become increasingly difficult to make an impact. The difference between famous and unknown YouTubers may lie in more than the quality of their videos. Are there any metrics in famous YouTubers' most viral videos - title, length, category, upload date - that set them apart from the rest? Could these metrics be used to create a guide for YouTubers who are starting out?


***


![image](images\sebastian-pandelache-taPBy6XyMoQ-unsplash.jpg)


# The story of Ada - Chapter 1: My first video

*Hi,*

*My name is Ada, I heard you were doing research on how small YouTubers can become successful, so that's why I reached out.*

*So here's the whole story: I'm a uni student, I like to make small vlogs about my daily life and share them with my friends. Some time ago, they suggested I put them on YouTube, which I thought was an exciting idea! Can you imagine, so many people around the world seeing my videos! So I've been uploading videos, but I've barely been getting any views... I'm so confused, what am I doing wrong? Vlogs are popular, plus I film with top-notch material and I work a lot on the editing too... Is there anything else which could help me grow my channel?*

*Thanks, Ada Westerlain*

![image](images\ada_part1_white.jpg)

# Evaluating relevant criteria for the success of a YouTube video

Dear Ada,

Thanks for reaching out to us! We’ve been hard at work on our analysis, and we’d love to use it to help you. :)
First of all, it's important to understand which "objective" parameters you can tune, as a content producer on youtube, to hopefully have a better performance in the long run. 
From the data we have access to as well as our knowledge of what potenciates engagement we selected four main parameters to study in depth: the titles of the videos, the tags used and, finally, the time constraints.
Firstly looking at the title, there are two main categories of features: its content and its shape.
For the content we chose to focus on referencing featutings, the use of different pronouns (with varying person and number) and the overall sentiment of the sentence (positive or negative). On the another hand, for the shape, the nuances taken into account were the number of words and the capitalization.
Secondly, regarding the use of tags, the analysis was performed on the number of tags used and on the specific tags that are most used.
At last, the time constraints refer to the duration of the videos and the posting frequency.
Let's now focus on how we handle the data.


# What data will we analyse?

To answer our questions, we will use a large dataset of YouTube channels and videos: YouNiverse. The dataset is divided into three main types of data: 
- Channel data, containing e. g. the date a channel registered on YouTube, its number of subscribers, etc.
- Video data, containing a video's title, its tags, its length and its number of views.
- Timeseries data, containing channels' weekly evolution (e. g. in terms of subscriber count) from 2015 to 2019.

{% include categories.html %}

We selected channels in the Entertainment category, which has the largest number of channels in the database and the least dependent on the "quality" of the content (music for example is really influenced by trends, politics by the view point taken on the given subject, and so on).

Then, we calculated a "growth score", that is, an indicator of the channels' success. The score was calculated by dividing the channel's number of subscribers in its latest entry of the timeseries by the number of days the channel was active (date of the latest timeseries - date of the channel's registration). We kept the 15% of channels with the best growth score as our "buzzing" channels (positive examples of success on youtube), and the 15% with the worst score as our "quiet" channels turning this into a binary problem easier to handle.

It's important to note that throughout this data exploration project, the mean of every feature was computed in order to attribute one value per feature per channel (for example the number of words of the title of a given channel is actually the mean of the number of words in the title of every video of that channel).

# A first glance at the features

After this explanation you probably want some actual high level tips to put to a test in your channel.

First of all, the title. The title of the video is one of the first things a potential viewer can see before clicking on your video (perhaps only second to the thumbnail of which we don't have an analysis unfortunatly:( ): it's bound to be important and most likely have a very palpable influence in how the video is received.
Here are the feature importances of the several parameters. These were calculated using a random forest algorithm to fitted to the data, much like a binary classification problem would work.

{% include title_features_importance.html %}

From this we can see that the number of words in the title clearly has a lot of influence on the result of the video. Let's see more specific values for this feature so you can apply it to your videos.

{% include boxplot_mean_numwords.html %}

As you can see in this boxplot the successful channels tend to have a few more words in their title, with a median of 10 words. We'd say this is due to a better ability to convey the content of the video if you use a couple more words, that is, describing better your content (perhaps using more exciting adjectives as well) could have a good effect on the views you get.

Let's go on to the tags! We studied the use of tags on our selected channels. To every video in the dataset, we assigned the value 1 if it included tags, and 0 if it did not include any tags. We then grouped the videos by channel and computed the average use of tags in the channel, ranging from 0 to 1. Here's what we found:

{% include boxplot_mean_is_tags.html %}

The results are clear: although both buzzing and quiet channels use tags in a large majority of their videos The median tag usage for buzzing channels is 1: this means that more than half of our buzzing channels use tags in every single one of their videos.

TODO: we should add something about the "time constraints" here i think the boxplot of the duration of the video is best because this should be a first set of tips that ADA can see the effect of right away (the frequency needs a bit more time to work)


# The story of Ada - Chapter 2: The importance of the title

*Hi!*

*Well, I've implemented what you talked about in my last couple videos and they did a bit better. I guess the effect of these changes will be potenciated as time goes on but i still think there's probably a few more tips you could give me in order to boost my next videos even more! What can you suggest? You talked about a few more features of the title, what were your conclusions on that?*

# Detailed title analysis

TODO: add the analysis of the other title features

mean_capital_title
mean_feats
mean_first_person_singular,mean_first_person_plural,mean_second_person,mean_third_person_singular,mean_third_person_plural

# The story of Ada - Chapter 3: The importance of the title

*Hi!*

*I’ve got good news: the videos I’ve posted since last time have been much more successful! I made sure to follow your advice about the title and the tags, you know adding relevant words and capitalization and all that. I’ve even got more than 100 subscribers now! Oh and don’t know if that helped, but I also changed the titles of my old videos - looking back, they were so bad hahaha*

*I think I could do even better though... Sometimes there's a big difference in the number of views I get on each video. One time I vlogged about my classes at uni, and that video totally flopped! And even my most viewed videos never go over a few thousand views... Am I just not making videos about lame topics or what?*

*Thank you so much! Ada*

![image](images\ada_part2.jpg)


# Topic analysis - Which topics are successful for Entertainment channels on YouTube?

TODO: describe the topic analysis as a response to Ada's question.

tags and sentiment analysis


# The story of Ada - Chapter 4: The buzz

TODO: Ada sends another message, she focused on more popular topics and her channel exploded

![image](images\ada_part3.jpg)

# Final tip - ensure long term success

TODO: post frequency

# Conclusion

TODO IF POSSIBLE: Include the interactive tool for predicting a video's success based on title, length...


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
