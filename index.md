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

After this first explanation, let's move on to some actual high level tips you can use in your channel's videos.

Here are the feature importances:

{% include features_importance.html %}

First of all, the title. The title of the video is one of the first things a potential viewer can see before clicking on your video (perhaps only second to the thumbnail, of which we unfortunately don't have an analysis): it's bound to be important and most likely have a very palpable influence in how the video is received.

We analyzed several parameters related to the videos' titles: the number of words, the usage of capital letters, the usage of the 'featuring' lexical field - which can indicate collaboration with other YouTubers or simply the presence of other guests, which pronouns are used in the title, and finally, sentiment analysis of words related to positive or negative emotions in the title.

We computed, for each channel, the mean of each of these parameters. Using this dataset of means across buzzing (1) and quiet (0) channels, we trained a random forest algorithm. This forest outputs whether or not a video title is likely to contribute to a video's success (1) or not (0), turning our title analysis into a simpler binary problem.

We then ordered the parameters by order of importance, that is, by how much each of them decreases the impurity in the random forest's classification. 

{% include title_features_importance.html %}

From this, we can see that among these parameters, the number of words in the title clearly has the most influence on the success of the video. Let's see more specific values for this feature so you can apply it to your own videos.

{% include boxplot_mean_numwords.html %}

As you can see in this boxplot, successful channels tend to have a few more words in their titles, with a median of 10 words. We'd say this is due to a better ability to convey the content of the video if you use a couple more words, that is, describing better your content (perhaps using more exciting adjectives as well) could have a good effect on the views you get.

Moreover, we studied the use of tags on our selected channels. To every video in the dataset, we assigned the value 1 if it included tags, and 0 if it did not include any tags. We then grouped the videos by channel and computed the mean use of tags across the channel's videos, ranging from 0 to 1. Here's what we found:

{% include boxplot_mean_is_tags.html %}

The results are clear: although both buzzing and quiet channels use tags in a large majority of their videos, buzzing channels use them much more consistently. Indeed, the median tag usage for buzzing channels is 1: this means that more than half of our buzzing channels use tags in every single one of their videos. If we look at the 25% quartile, the difference becomes even more drastic: it has a value of 0.985 for the buzzing channels - meaning three quarters or more of these channels use tags in at least 98.5% of their videos - while having a value of only 0.843 for quiet channels.

The importance of using tags makes a lot of sense with regards to YouTube's search engine: although they are barely visible to viewers, tags help categorise the video and will make it more likely to appear in the search results of a related query.

Let's now take a look at the average duration of the videos. We found that successfull channels have videos slightly longer than other channels. 

As you can see unsuccessfull channels have videos that on average are three minutes shorter. From the buzzing channels we can conclude that a duration of around eight minutes is the median and ten minuts is the one that works best!

TODO: add boxplot for the mean duration, i couldnt render the "pretty" ones, only the regulars


# The story of Ada - Chapter 2: The importance of the title

*Hi!*

*Well, I've implemented what you talked about in my last couple videos and they did a bit better. I guess the effect of these changes will be potenciated as time goes on but i still think there's probably a few more tips you could give me in order to boost my next videos even more! What can you suggest? You talked about a few more features of the title, what were your conclusions on that?*

# Detailed title and tag analysis

Hello again Ada, 

You're right, there's still some work to do. Let's talk about capitalization, sentiment, featurings, pronouns and number of tags.

For featurings unfortunatly we didn't see much difference in use between buzzing and quite channels. 

TODO: was there any interesting conclusion about pronoun use?

Similarly, for sentiment analysis of the title, the only thing we were able to conclude is that it doesn't really matter the sentiment, what matters most is using more words that describe it, for example more positive/negative adjectives.

On the other hand, capitalization of the words in the title seems to have a positive effect on the outcome. On average successful channels have 30% of capitalization and quite ones only 20%. Here are the results:

TODO: add boxplot for the capitalization, i couldnt render the "pretty" ones, only the regulars

Finaly for the tags. We've seen the importance of adding tags to your videos but how many should you add? On average buzzing channels will have around 20 tags per video and quite ones only have half of that! This is an interesting conclusion as now you can tune the number of tags you use to potentiate visibility of the channel!

TODO: add boxplot for the number of tags, i couldnt render the "pretty" ones, only the regulars

# The story of Ada - Chapter 3: The importance of the title

*Hi!*

*I’ve got good news: the videos I’ve posted since last time have been much more successful! I made sure to follow your advice about the title and the tags, you know adding relevant words and capitalization and all that. I’ve even got more than 100 subscribers now! Oh and don’t know if that helped, but I also changed the titles of my old videos - looking back, they were so bad hahaha*

*I think I could do even better though... Sometimes there's a big difference in the number of views I get on each video. One time I vlogged about my classes at uni, and that video totally flopped! And even my most viewed videos never go over a few thousand views... Am I just making videos about lame topics or what?*

*Thank you so much! Ada*

![image](images\ada_part2_white.jpg)


# Topic analysis - Which topics are successful for Entertainment channels on YouTube?

TODO: describe the topic analysis as a response to Ada's question.

Dear Ada,

First of all, we're happy that our advice could help! Congrats on passing the bar of 100 subscribers, that's already an impressive milestone.

Now, about the difference in views across your videos, this can definitely be linked to the topics you present in each of them. Naturally, trending topics change over time, but we noticed a few topics that appear consistently in our buzzing channels' videos. We studied the distribution of tags in both buzzing and quiet channels, and compiled the most used tags in both.

![image](output/tags_quiet.png)

![image](output/tags_buzz.png)

If we exclude stopwords such as "the" or "of", we observe that most of the common tags appear in both buzzing and quiet channels. This overlap makes sense due to the size of the database of channels: there are simply too many videos for every single one of them to be successful. We still notice, however, that certain tags appear in the buzzing list but not in the quiet one: among these, "challenge" or "prank" might be tags of interest to your channel. Of course, it can also be effective to add other tags that belong to both lists, as they will improve the referencing of your video.

{% include buzz_topics.html %}

{% include quiet_topics.html %}

# The story of Ada - Chapter 4: The buzz

*Hi!!*

*So I made a new video: I put together some of the topics you suggested. And you know what? It got over 30'000 views, I can't believe it!*

*I also made a few more videos about uni, actually. I love my classes and missed talking about them in my vlogs...*

![image](images\ada_part3_white.jpg)

# Final tip - ensure long term success

We are very pleased to hear that everything is working out for the best with your youtube channel, and very pround to see that our work has an impact in the real world!

We'll leave you with a final tip! One of the findings we came up with in our analysis was that the frequency with which a youtuber posts is different between successfull and not so successfull content creators. 

Over 50% of buzzing channels post more than one video per week (the median is 1.4), as for the quiet ones the median is 0.5 meaning there are even weeks with no new videos. 

Keeping up with your audience and consistently sharing content proves to be a great way to ensure long term success as your viewers will connect to you and your content in a more meaningful way. 

Having, for example, a well known post schedule is a good way to mantain engagement high and make sure that your base audience always watches your vides since they will be looking forward to that day of the week they know you will post.

Take a look at the values in the following graph!

{% include boxplot_week_freq.html %}

# Conclusion

We can conclude from this analysis that, even though the most relevant predictor for success on youtube is the content itself and its quality, there are still some objective parameters that, if tuned correctly, will amplify the reach of our channel and generate more engagement, making the number of views and subcribers grow faster.

Here is the recipe we found the buzzing channels are following:
 - Around 10 words in the title
 - At least 30% of capitalization of the words of the title
 - Always use tags in the videos
 - Around 20 tags per video 
 - At least 1 video per week, but it's better if you can do more
 - Around 10 minutes of video duration

TODO: Add something about the topic analysis

TODO IF POSSIBLE: Include the interactive tool for predicting a video's success based on title, length...




![image](output/venn_lexical.png)
![image](output/wordcloud_tags_buzz.png)
![image](output/wordcloud_tags_quiet.png)

![image](output/relative_use_lexical.png)

![image](output/evolution_sub_ytb.png)
{% include adas-evolution.html %}


<script src="https://gist.github.com/zwierski/fe66b9662878b9f29f9a231190e215d2.js"></script>
