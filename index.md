***

# Abstract
Nowadays, anyone with a smartphone and an Internet connection can become a YouTuber. Many beginners dream of success on the platform, with videos acclaimed by millions of subscribers. However, reaching fame is not as easy as it seems: indeed, with how much the number of creators has grown in the past years, it has become increasingly difficult to make an impact. The difference between famous and unknown YouTubers may lie in more than the quality of their videos. Are there any metrics in famous YouTubers' most viral videos - title, length, category, upload date - that set them apart from the rest? Could these metrics be used to create a guide for YouTubers who are starting out?


***


![image](images\sebastian-pandelache-taPBy6XyMoQ-unsplash.jpg)


# The story of Ada - Chapter 1: My first video and importance of the title

*Hi,*

*My name is Ada, I heard you were doing research on how small YouTubers can become successful, so that's why I reached out.*

*So here's the whole story: I'm a uni student, I like to make small vlogs about my daily life and share them with my friends. Some time ago, they suggested I put them on YouTube, which I thought was an exciting idea! Can you imagine, so many people around the world seeing my videos! So I've been uploading videos, but I've barely been getting any views... I'm so confused, what am I doing wrong? Vlogs are popular, plus I film with top-notch material and I work a lot on the editing too... Is there anything else which could help me grow my channel?*

*Thanks, Ada Westerlain*

![image](images\ada_part1_white.jpg)

# Evaluating relevant criteria for the success of a YouTube video

Dear Ada,

Thanks for reaching out to us! We’ve been hard at work on our analysis, and we’d love to use it to help you. :)
We believe it's important to understand which "objective" parameters you can tune, as a content producer on YouTube, to hopefully have a better performance in the long run. 

But first, let's explain to you what kind of data we used for our research.

# What data will we analyse?

To answer our questions, we will use a large dataset of YouTube channels and videos: YouNiverse. The dataset is divided into three main types of data: 
- Channel data, containing e. g. the date a channel registered on YouTube, its number of subscribers, etc.
- Video data, containing a video's title, its tags, its length and its number of views.
- Timeseries data, containing channels' weekly evolution (e. g. in terms of subscriber count) from 2015 to 2019.

{% include categories.html %}

We selected channels in the Entertainment category, which has the largest number of channels in the database and the least dependent on the "quality" of the content (music for example is really influenced by trends, politics by the view point taken on the given subject, and so on). Moreover, your vlog channel definitely fits into this category, so we are confident our analysis will be relevant to your content.

To quantify a channel's success, we calculated a "growth score". This score was calculated by dividing the channel's number of subscribers in its latest entry of the timeseries by the number of days the channel was active (date of the latest timeseries - date of the channel's registration). We kept the 15% of channels with the best growth score as our "buzzing" channels (positive examples of success on youtube), and the 15% with the worst score as our "quiet" channels turning this into a binary problem easier to handle.

It's important to note that throughout this data exploration project, the mean of every feature was computed in order to attribute one value per feature per channel (for example the number of words of the title of a given channel is actually the mean of the number of words in the title of every video of that channel).

# Importance of the title

After this first explanation, let's move on to some actual high level tips you can use in your channel's videos.

Here are the feature importances:

{% include features_importance.html %}

First of all, there's one thing we immediately noticed in the video you sent us: the title "day at my uni", while relevant and to the point, could be tweaked a little to be more attractive to your viewers.

Indeed, the title of a video is one of the first things a potential viewer can see before clicking on your video (perhaps only second to the thumbnail, of which we unfortunately don't have an analysis). It's bound to be important and most likely have a very palpable influence in how the video is received.

We analyzed several parameters related to the videos' titles: the number of words, the usage of capital letters, the usage of the 'featuring' lexical field - which can indicate collaboration with other YouTubers or simply the presence of other guests, which pronouns are used in the title, and finally, the presence of words related to positive or negative emotions in the title.

We computed, for each channel, the mean of each of these parameters. Using this dataset of means across buzzing (1) and quiet (0) channels, we trained a random forest algorithm. This forest outputs whether or not a video title is likely to contribute to a video's success (1) or not (0), turning our title analysis into a simpler binary problem.

We then ordered the parameters by order of importance, that is, by how much each of them decreases the impurity in the random forest's classification. 

{% include title_features_importance.html %}

From this, we can see that among these parameters, the number of words in the title clearly has the most influence on the success of the video. Let's see more specific values for this feature so you can apply it to your own videos.

{% include boxplot_mean_numwords.html %}

As you can see in this boxplot, successful channels tend to have a few more words than quiet channels in their videos' titles, with a median of 10 words. We'd say this is due to a better ability to convey the content of the video if you use a couple more words: that is, describing your content in more detail - perhaps using more exciting adjectives as well - could boost your video's views.

For featurings unfortunatly we didn't see much difference in use between buzzing and quiet channels. Besides, as you're only starting out, don't worry about collaborating with other YouTubers yet.

TODO: was there any interesting conclusion about pronoun use?

Similarly, for sentiment analysis of the title, the only thing we were able to conclude is that it doesn't really matter the sentiment, what matters most is using more words that describe it, for example more positive/negative adjectives.

On the other hand, capitalization of the words in the title seems to have a positive effect on the outcome. On average successful channels have 30% of capitalization and quite ones only 20%. Here are the results:

TODO: add boxplot for the capitalization, i couldnt render the "pretty" ones, only the regulars

Finaly for the tags. We've seen the importance of adding tags to your videos but how many should you add? On average buzzing channels will have around 20 tags per video and quite ones only have half of that! This is an interesting conclusion as now you can tune the number of tags you use to potentiate visibility of the channel!

TODO: add boxplot for the number of tags, i couldnt render the "pretty" ones, only the regulars

TODO: add boxplot for the mean duration, i couldnt render the "pretty" ones, only the regulars


Let's now take a look at the average duration of the videos. We found that successfull channels have videos slightly longer than other channels. 

As you can see unsuccessful channels have videos that on average are three minutes shorter. From the buzzing channels we can conclude that a duration of around eight minutes is the median and ten minuts is the one that works best!


# The story of Ada - Chapter 2: Trending topics?

*Hi!*

*I’ve got good news: the new videos I’ve posted since last time have been quite successful! I made them shorter than the uni vlog (around 10 minutes like you suggested), and I made sure to follow your advice about the title, you know adding around 10 words and capitalization and all that. I’ve even gotten a few subscribers now! Oh and don’t know if that helped, but I also changed the titles of my old videos - looking back, they were so bad hahaha*

*I think I could do even better though... Sometimes there's a big difference in the number of views I get on each video. One time, I vlogged about a sports challenge I participated in, and got over 100 views! But another time, I made a video about some comments I got on Instagram, and that one totally flopped! And even my most viewed videos never go over a few thousand views... Am I just making videos about lame topics or what?*

![image](images\ada_part2_white.jpg)

# Topic analysis - Which topics are successful for Entertainment channels on YouTube?

Dear Ada,

First of all, we're happy that our advice could help! Congrats on getting some subscribers, that's already a promising milestone!

Now, about the difference in views across your videos, this can definitely be linked to the topics you present in each of them. Naturally, trending topics change over time, but we noticed a few topics that appear consistently in our buzzing channels' videos. In the following graphs, you can see which topics appear the most in buzzing channels and quiet channels, their appearance being represented by a mean score.

{% include buzz_topics.html %} {% include quiet_topics.html %}

You will notice that buzzing and quiet channels tend to tackle similar topics. However, some of the topics are more represented in the 

This overlap makes sense due to the size of the database of channels: there are simply too many videos for every single one of them to be successful.

![image](output/relative_use_lexical.png)



# The story of Ada - Chapter 3: Don't forget the tags!

*Wait, I actually have another question. Even my videos about trending topics never go over a few hundreds of views... Is there something else I'm missing even though I'm using enough trendy words in my titles? Maybe it's the description... I guess I don't spend enough time on it.*

*Thanks again! Ada*



Dear Ada,

Your question is very relevant! Thinking about the description is a good insight, as well, because another relevant feature we studied is closely related to it: the video's tags.

Intuitively, we can assume the importance of using tags makes a lot of sense with regards to YouTube's search engine: although they are barely visible to viewers, tags help categorise the video and will make it more likely to appear in the search results of a related query.

To analyse this assumption, we studied the usage of tags in our dataset's channels. To every video in the dataset, we assigned the value 1 if it included tags, and 0 if it did not include any tags. We then grouped the videos by channel and computed the mean use of tags across the channel's videos, ranging from 0 to 1. Here's what we found:

{% include boxplot_mean_is_tags.html %}

The results are clear: although both buzzing and quiet channels use tags in a large majority of their videos, buzzing channels use them much more consistently. Indeed, the median tag usage for buzzing channels is 1: this means that more than half of our buzzing channels use tags in every single one of their videos. If we look at the 25% quartile, the difference becomes even more drastic: it has a value of 0.985 for the buzzing channels - meaning three quarters or more of these channels use tags in at least 98.5% of their videos - while having a value of only 0.843 for quiet channels.

Now, you might wonder which tags to use. To answer this question, we studied the distribution of tags in both buzzing and quiet channels, and compiled the most used tags in both.

![image](output/tags_buzz.png)

![image](output/tags_quiet.png)

If we exclude stopwords such as "the" or "of", we observe that most of the common tags appear in both buzzing and quiet channels. This overlap makes sense due to the size of the database of channels: there are simply too many videos for every single one of them to be successful. We still notice, however, that certain tags appear in the buzzing list but not in the quiet one: among these, "challenge" or "prank" might be tags of interest to your channel. Of course, it can also be effective to add other relevant tags that belong to both lists, as they will improve the referencing of your video.

Moreover, unlike the title, tag words do not need to be exactly relevant to your video's topic. Of course, it's not a good practice to add too many tags that have nothing to do with your video: YouTube even deems this kind of "tag spamming" to be against its terms of service. Still, without resorting to spamming, don't hesitate to branch out and add a few general words to your tags! For example, you could definitely add the word "fun" to your sports challenge video's tags, on top of the more relevant "vlog" and "challenge" (which is a topic very present in buzzing channels, lucky!).

We will give you wordclouds of the most used tags in buzzing and quiet channels, as a visual reminder.

![image](output/wordcloud_tags_buzz.png)
![image](output/wordcloud_tags_quiet.png)

Good luck with tagging your videos, Ada! We look forward to hearing again from you.


# The story of Ada - Chapter 4: The buzz

*Hi!!*

*So I made a new video: I put together some of the topics you suggested. And you know what? It got over 30'000 views, I can't believe it!*

*I also made a few more videos about uni, actually. I love my classes and missed talking about them in my vlogs... Unlike the first time, though, I made sure to pick a more attractive title, make the video shorter and use a bunch of tags. And they did pretty well! Maybe it's because I have more subscribers now, but I'm sure it's thanks to your advice too!*

![image](images\ada_part3_white.jpg)

# Final tip - ensure long term success

We are very pleased to hear that everything is working out for the best with your youtube channel, and very pround to see that our work has an impact in the real world!

We'll leave you with a final tip! One of the findings we came up with in our analysis was that the frequency with which a youtuber posts is different between successful and not so successful content creators. 

{% include boxplot_week_freq.html %}

Over 50% of buzzing channels post more than one video per week (the median is 1.4), as for the quiet ones the median is 0.5 meaning there are even weeks with no new videos. 

Keeping up with your audience and consistently sharing content proves to be a great way to ensure long term success as your viewers will connect to you and your content in a more meaningful way. 

Having, for example, a well known post schedule is a good way to mantain engagement high and make sure that your base audience always watches your vides since they will be looking forward to that day of the week they know you will post.

# Conclusion

We can conclude from this analysis that, even though the most relevant predictor for success on youtube is the content itself and its quality, there are still some objective parameters that, if tuned correctly, will amplify the reach of our channel and generate more engagement, making the number of views and subcribers grow faster.

Here is the recipe we found the buzzing channels are following:
 - Around 10 words in the title,
 - At least 30% of capitalization of the words of the title,
 - Always use tags in the videos,
 - Around 20 tags per video,
 - At least 1 video per week, but it's better if you can do more,
 - Video duration around 10 minutes.

TODO: Add something about the topic analysis

TODO IF POSSIBLE: Include the interactive tool for predicting a video's success based on title, length...




![image](output/venn_lexical.png)
![image](output/wordcloud_tags_buzz.png)
![image](output/wordcloud_tags_quiet.png)

![image](output/relative_use_lexical.png)

![image](output/evolution_sub_ytb.png)
{% include adas-evolution.html %}


<script src="https://gist.github.com/zwierski/fe66b9662878b9f29f9a231190e215d2.js"></script>
