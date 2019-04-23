# Gendered Interaction Online: Final Report
Katie Thomas  
kdt13@pitt.edu

## Motivation and Background Information

## Data

### Data Source
I found my original data from a study done at Stanford University, called [RtGender](https://nlp.stanford.edu/robvoigt/rtgender/). At the bottom of the linked page, you can download the data yourself as long as you sign and agree to use the data for non-commercial research purposes only. This data includes csv files of posts and their corresponding responses from Facebook, TED, Fitocracy, and Reddit.

### Data Cleanup
My goal for the cleanup was to combine the information about the posts into the information about the responses - keeping each individual source separate, as they had slightly different formats. Thus, the cleanup process was somewhat lengthy as I had to examine the best way to merge each file.

#### Facebook Congress
These files were from Facebook, comprised of posts from members of Congress, as well as responses to these posts. The gender is visible for the poster, but not for the responder. Many posts had many responses. I merged on the column called "post_id", as I discovered it was unique to the post in both post and response files. I also filled the nulls with empty strings, since there could be some other worthwhile information in the same row. There also arose an interesting problem, when I realized that sometimes there were duplicate post text values, that were basically the same post by the same person but assigned to a different post ID. I did my best to remove these, making sure that they weren't removed if there was a response attached to it or if they were the first occurrence of the duplicate.

#### Facebook Wiki
Facebook Wiki files were composed of Facebook posts as well, except this time there was a wider range of industries represented (taken from Wikipedia category pages, like "male tennis players"). The gender is again only visible for the poster. These files were formatted in the same manner as the Facebook Congress files, so I faced some of the same challenges. Again, I merged on post ID and filled nulls with empty strings. Additionally, there were also some strange duplicate values of post text that I deleted in the same manner.

#### Fitocracy
Fitocracy is a fitness social media page, where people can discuss fitness, progress, etc. This time, genders were always visible (for both poster and responder!) and there was only one response per post. I again merged on post ID, as it was unique to the post. There were some duplicates that seemed like automated posts ("Welcome to Fitocracy group!"), but the corresponding responses seemed to be unique, so I didn't get rid of duplicate posts this time.

#### Reddit
These files were composed of Reddit posts and responses from a variety of subreddits. Again, there was only one response per post. However, a difference in this file was that the responder's gender was only known sometimes. I could again merge on post ID, and had to fill a few nulls. The duplicates in this case seemed relatively normal, so I again did not get rid of duplicate posts.

#### TED
This file only contains responses, as it was taken from responses to TED talks. Since these are videos, there was no post text. This time, the gender of the speaker was known, but not the gender of the responder. There were a few nulls to fix, as well as some formatting errors, but this time there was no merging necessary.

## Analysis

### Overview

### Linguistic Analysis by Gender

### Gender x Gender Analysis

### Machine Learning

## Conclusion

