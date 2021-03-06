# Gendered Interaction Online: Final Report
Katie Thomas  
kdt13@pitt.edu

## Motivation and Background Information
How do men and women present themselves differently online? Do people respond differently to male vs. female posters? Do male/female responders respond differently depending on the gender they are responding to? These are some initial questions I had when thinking about this project. After reading up on some sociolinguistic literature (*Women, Men, and Language*, by Jennifer Coates), I came up with a few ideas of what to look at. Some notable differences that were discussed were hedges, compliments, and questions. It is thought that women use more hedges, i.e., phrases that express uncertainty, than men, which is possibly due to the fact that they are socialized to believe asserting themselves isn't "ladylike." Also, women tend to give and receive more compliments than men. Additionally, women tend to use more questions that "avoid the role of expert" (i.e., isn't it? don't you? etc.) than men.

## Data
I found my original data from a study done at Stanford University, called [RtGender](https://nlp.stanford.edu/robvoigt/rtgender/). At the bottom of the linked page, you can download the data yourself as long as you sign and agree to use the data for non-commercial research purposes only. This data includes csv files of posts and their corresponding responses from Facebook, TED, Fitocracy, and Reddit.

### Data Cleanup
My goal for the cleanup was to combine the information about the posts into the information about the responses - keeping each individual source separate, as they had slightly different formats. Thus, the cleanup process was somewhat lengthy as I had to examine the best way to merge each file.

#### [Facebook Congress](https://nbviewer.jupyter.org/github/Data-Science-for-Linguists-2019/Gendered-Interaction-Online/blob/master/exploratory_data_analysis/modifying_dataset.ipynb#Facebook-Congress-posts-and-responses)
These files were from Facebook, comprised of posts from members of Congress, as well as responses to these posts. The gender is visible for the poster, but not for the responder. To merge these, I merged the post data into the response data, as sometimes there were posts with multiple responses. There arose an interesting problem, when I realized that sometimes there were duplicate post text values, that were basically the same post by the same person but assigned to a different post ID. I did my best to remove these, making sure that they weren't removed if there was a response attached to it or if they were the first occurrence of the duplicate.

#### [Facebook Wiki](https://nbviewer.jupyter.org/github/Data-Science-for-Linguists-2019/Gendered-Interaction-Online/blob/master/exploratory_data_analysis/modifying_dataset.ipynb#Facebook-wiki-posts-and-responses)
Facebook Wiki files were composed of Facebook posts as well, except this time there was a wider range of industries represented (taken from Wikipedia category pages, like "male tennis players"). The gender is again only visible for the poster. These files were formatted in the same manner as the Facebook Congress files, so I faced some of the same challenges. Again, I merged into the response file. Additionally, there were also some strange duplicate values of post text that I deleted in the same manner.

#### [Fitocracy](https://nbviewer.jupyter.org/github/Data-Science-for-Linguists-2019/Gendered-Interaction-Online/blob/master/exploratory_data_analysis/modifying_dataset.ipynb#Fitocracy-posts-and-responses)
Fitocracy is a fitness social media page, where people can discuss fitness, progress, etc. This time, genders were always visible (for both poster and responder!) and there was only one response per post, making it a little more simple to merge. There were some duplicates that seemed like automated posts ("Welcome to Fitocracy group!"), but the corresponding responses seemed to be unique, so I didn't get rid of duplicate posts this time.

#### [Reddit](https://nbviewer.jupyter.org/github/Data-Science-for-Linguists-2019/Gendered-Interaction-Online/blob/master/exploratory_data_analysis/modifying_dataset.ipynb#Reddit-posts-and-responses)
These files were composed of Reddit posts and responses from a variety of subreddits. Again, there was only one response per post, so I merged similarly. However, a difference in this file was that the responder's gender was only known sometimes. The post duplicates in this case seemed relatively normal, so I again did not get rid of duplicate posts.

#### [TED](https://nbviewer.jupyter.org/github/Data-Science-for-Linguists-2019/Gendered-Interaction-Online/blob/master/exploratory_data_analysis/modifying_dataset.ipynb#TED-responses)
This file only contains responses, as it was taken from responses to TED talks. Since these are videos, there was no post text. This time, the gender of the speaker was known, but not the gender of the responder. There was no merging necessary with this file, as there is a singular response file.

## Hypothesis
Coates' literature allowed me to formulate a more specific hypothesis regarding my data:

1. Responders "favor" their own gender. I was unsure of the specifics of this, since it's very vague, but I thought there would be a notable difference in how female responders responded to other females vs. males, and in how male responders responded to other males vs. females.
2. Women use more hedges than men.
3. Women use more questions that "avoid the role of expert" than men.

## Analysis
An important question to ask is whether the poster's gender is visible to the responder, as that is necessary for some of the following analysis. For the two Facebook files, since the posts are from known people, the gender is known and available to the responders. For Fitocracy, I examined the setup of the website, and discovered that the gender is visible on the person's profile. This could be potentially problematic (since it isn't directly visible on the post), but many users also have pictures of themselves so gender can be inferred from the pictures, as well as clicking on the user's profile. For Reddit, I made sure to filter for "op_gender_visible," meaning the responder is able to see the poster's gender.

### Preliminary Analysis
I started with some basic analysis (located [here](https://nbviewer.jupyter.org/github/Data-Science-for-Linguists-2019/Gendered-Interaction-Online/blob/master/main_analysis.ipynb#Conduct-basic-analysis)) of each file so I could better understand what I was working with. One important thing to note is the gender distributions, as this is very important to my analysis. Fitocracy was the only file that this was close to being an equal distribution. Facebook Congress, Reddit, and TED were very male dominated, whereas Facebook Wiki was more female dominated.

Something interesting to note is how male-dominated Reddit actually is. Out of 98 subreddits, only five (BigBrother, awww, counting, relationships, and rupaulsdragrace) had more female posters than male posters. Below is a graph of the first 20 subreddits to get an idea of how many more male posters there are, normalized for total number of posts in the subreddit.

![png](images/subreddits_normalized.png)

### Linguistic Analysis by Gender
I then moved onto some linguistic analysis, located [here](https://nbviewer.jupyter.org/github/Data-Science-for-Linguists-2019/Gendered-Interaction-Online/blob/master/main_analysis.ipynb#Conduct-linguistic-analysis). This is again broken up into the separate data source files. However, before conducting analysis, I reduced the sizes of the files down to 50,000, as some of them were huge and would take a very large amount of time to do something like word tokenization. For my linguistic analysis, I calculated text length, average sentence length, and average Google k-band. I also used t-tests to determine the significance of these differences by gender.

Overall, it seems that female posters and responders had longer posts/responses, as well as longer sentences. This was especially prominent in Facebook Congress, Fitocracy, and Reddit. Facebook Wiki was opposite (male posters had longer posts and sentences) and TED was not significant. Also, in Fitocracy and Reddit, the responses to female posters were longer than responses to male posters. There was never any significance in the TED file.

For hedges, (analysis starting [here](https://nbviewer.jupyter.org/github/Data-Science-for-Linguists-2019/Gendered-Interaction-Online/blob/master/main_analysis.ipynb#Linguistic-difference-in-gender)), I created functions to search for them in the text. I searched for "I think", "I guess", "I mean", "kind of", "I'm sure", "you know", "sort of", "perhaps", and "maybe". This is of course not an exhaustive list, but these are some common ones that people use. When conducting the analysis, female posters/responders seem to dominate once again, but it's less prominent. Female posters use more hedges in Facebook Congress and Reddit, and female responders use more hedges in Reddit as well. Male posters only use more hedges in Facebook Wiki, and there was no significance for Fitocracy. For my question analysis, I did not find any significance in the use between male and female posters.

### Gender x Gender Analysis
For this analysis, we can only look at Fitocracy and Reddit files, because they are the only ones that we know the gender of both poster and responder.

#### Response text length and response sentence length
In the [Fitocracy file](https://nbviewer.jupyter.org/github/Data-Science-for-Linguists-2019/Gendered-Interaction-Online/blob/master/main_analysis.ipynb#Fitocracy-linguistic-analysis), male responders have longer responses and sentences when responding to males than when responding to females and female responders have longer responses and sentences when responding to females than when responding to males. See the below boxplots:

| Response text length                            | Response sentence length                      |
| :---------------------------------------------: | :-------------------------------------------: |
| ![png](images/fit_response_length_bygender.png) | ![png](images/fit_response_slen_bygender.png) |

[Reddit](https://nbviewer.jupyter.org/github/Data-Science-for-Linguists-2019/Gendered-Interaction-Online/blob/master/main_analysis.ipynb#Reddit-linguistic-analysis) is somewhat the opposite, as this time male responders have longer responses when responding to females than when responding to males. However, this time, there isn't a significant difference in the length of female responses, and the response sentence lengths are never significant. See the below boxplot for response length:

![png](images/reddit_response_length_bygender.png)

In summary, this somewhat matches my hypothesis of same genders "favoring each other." When the results are significant, they are more often male-to-male or female-to-female than opposite genders. However, there are still a good amount of insignificant results.

#### Exploration
As another addition to my Gender x Gender analysis, I decided to quickly look at the presence of a few specific words that were "stereotypical" (file located [here](https://nbviewer.jupyter.org/github/Data-Science-for-Linguists-2019/Gendered-Interaction-Online/blob/master/genderxgender.ipynb)). First, I decided to look at stereotypical male-to-male language ("bro", "dude", and "man") and female-to-female language ("girly", "girlie", "chica"). Female-to-female was a little more difficult to come up with, as I don't think they are as prominent. I originally had "girl" in the list of female-to-female language, but it turned out that it was such a common word that male posters used it just as frequently, if not more. Thus, I took out "girl" and got a more reasonable result. Below are the graphs of percentages of posters using this language:

| Male to male (bro, dude, and man)   | Female to female (girly, girlie, and chica)   |
| :---------------------------------: | :-------------------------------------------: |
| ![png](images/maletomale.png)       | ![png](images/femaletofemale2.png)            |

As we can see, the male-to-male language is dominated by male responders responding to male posters, and the female-to-female language is dominated by female responders responding to female posters.

I also examined singular words/phrases: "beautiful", "sexy", and "good job". The dominating group for using "beautiful" was female-to-female, followed by male-to-female. The dominating group for using "sexy" was male-to-female, followed by female-to-male. Lastly, the dominating group for using "good job" was male-to-male, followed closely by female-to-female.

### Machine Learning
I had two original goals for machine learning:

1. Predict the gender of the poster/responder, regardless of whether it was from a poster or responder
2. Predict the gender of both the poster and the responder, only given the response text

For my first goal, I [created a new dataframe](https://nbviewer.jupyter.org/github/Data-Science-for-Linguists-2019/Gendered-Interaction-Online/blob/master/main_analysis.ipynb#Goal-1) by combining the samples from the different sources. The baseline here was 63% male. Using Naive Bayes, I was able to [fit a model](https://nbviewer.jupyter.org/github/Data-Science-for-Linguists-2019/Gendered-Interaction-Online/blob/master/machine_learning.ipynb#Predict-gender-of-poster/responder) to achieve about 71% accuracy. This involved using nltk's tokenizer, as I discovered that keeping punctuation actually aided the classifier. Below is the confusion matrix.

![png](images/predict_1gender_cm.png)

As we can see, it still struggles to classify female posters, but we do have some increase in accuracy from the baseline. I quickly examined some puncutation use as well, and discovered that female posters and responders seemed to be more likely to use exclamation points (especially two in a row!!).

For my second goal, I also [created a new dataframe](https://nbviewer.jupyter.org/github/Data-Science-for-Linguists-2019/Gendered-Interaction-Online/blob/master/main_analysis.ipynb#Goal-2) by combining the data that had both genders known (Fitocracy and Reddit only). The baseline here was 38% male responding to male. Using Naive Bayes, I was able to [fit a model](https://nbviewer.jupyter.org/github/Data-Science-for-Linguists-2019/Gendered-Interaction-Online/blob/master/machine_learning.ipynb#Predict-both-genders) to achieve about 47% accuracy. Below is the confusion matrix.

![png](images/predict_2genders_cm.png)

This is clearly not a very high accuracy score, but it is higher than the baseline by about 9 percentage points. I figured this would be the most difficult task, as there are four different possible labels to predict (MM, MW, WM, WW), and the classifier was only given the response text.

Lastly, I came up with another goal to [predict only the poster's gender](https://nbviewer.jupyter.org/github/Data-Science-for-Linguists-2019/Gendered-Interaction-Online/blob/master/machine_learning.ipynb#Predict-poster-gender) given the response text, in an attempt to simplify the last task. The baseline here was about 62%. However, using the same algorithm, I only achieved about 65% accuracy. Below is the confusion matrix.

![png](images/predict_poster_cm.png)

Identifying gender based on text alone seems like a very difficult task, especially when we are trying to predict the gender of the person the responder is responding to.

## Conclusion

### Difficulties
Something that I had wanted to analyze but didn't get around to was looking at compliments. I had initially included in my hypothesis that women would give and receive more compliments, but this seemed more difficult to analyze. For example, one way that I could think of analyzing this is to physically annotate occurrences of compliments, and then examine what genders and giving and receiving these compliments. This would take a very long time though, and I didn't get into it for my analysis.

Another difficulty I faced was the analysis of question use. It was hard to come up with questions that would be used in an "avoiding the role of expert" context. Thus, my list of question words was very short and results were insignificant. I included were "do you?", "don't you?", "aren't there?", and "isn't it?". Some p-values seemed to be low enough, but the questions were present so infrequently (less than 0.1%) that I made the decision to not count any of them as significant. To more formally do this, annotation would again make more sense.

I also wish that my machine learning results were more significant. Something that I struggled with was adding other features. I [used hstack](https://nbviewer.jupyter.org/github/Data-Science-for-Linguists-2019/Gendered-Interaction-Online/blob/master/machine_learning.ipynb#Try-adding-other-features) to try to add features for text length, but my accuracy score actually ended up being lower than the baseline. Predicting gender seems to be a difficult task, but I wish there would have been more prominent results.

### End Results
There were a good amount of significant findings that resulted from this project. For this summary, I will be going over the results that were present in the majority (but not all) of the files. Female posters/responders seemed to have longer posts and use longer sentences in general than male posters/responders. Female posters/responders also seemed to use more hedges in general than male posters/responders. It also seems that it's more likely that people will have longer responses and use longer sentences when they are responding to someone of the same gender as themselves.

Parts of my hypothesis are supported - same genders "favor" each other (i.e., use longer posts) and female posters use more hedges. However, I would have liked to go more in depth about same-gender interaction. I briefly discussed male-to-male and female-to-female language, but there are sure to be other qualities that this gender interaction exhibits. There is still a lot to learn about how different genders interact online. This data didn't contain age information, but it would likely be a contributing factor to how people respond as well. Additionally, hedges, questions, and compliments could be looked into further in depth.
