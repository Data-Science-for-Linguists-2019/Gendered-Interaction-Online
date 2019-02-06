# Gendered Interaction Online: Project Plan

## Goals for the project
I have two main goals for my project:
1. Look at
look at GENDER X GENDER
machine learning - guess gender of poster and gender of responder?
still unsure if I want to do anything with sentiment

## Preparing for the study
To prepare for this study and the creation of my hypotheses, I need to read up on some sociolinguistics papers about gender. I can also read over the paper that accompanies the data set I am using (https://nlp.stanford.edu/robvoigt/rtgender/rtgender.pdf), however, I don't want to just replicate their results. I would like to understand what they did and base my research off of it, but also dive in deeper to some things that were left unexplored (more specific goals outlined later).

## Data set

### Source
The data set I will be using is called RtGender, found here: https://nlp.stanford.edu/robvoigt/rtgender/. This data set contains csv files of posts and responses on social media. It contains 10 csv files of interactions on Facebook, Fitocracy, Reddit, and TED, as well as a file annotated for sentiment and relevance. In the files, the gender of the poster is always included, but the gender of the responder is only available sometimes.

### Cleaning up data
This corpus is extremely large (5.66 GB, contains more than 25M comments). I thought it might be a good idea to exclude when we don't know the gender of the responder, which eliminates most of the data (which is probably okay anyways, since there was so much data to begin with). It would get the data set down to something more manageable, while still being large enough to be able to draw some conclusions. This also allows us to narrow the scope on our analysis.

The files that contain the gender of the responder are:
- Fitocracy posts and responses: From my quick examination, it seems that all, or almost all, of the posts contain the gender of the responder. According to the research paper, there are 318,536 status updates in this file.
- Reddit posts and responses: Only some of the posts contain the gender of the responder. According to the research paper, there are 1,453,512 post-response pairs, with only about 9.2% having the responder gender tagged. However, this still gives us more than 133,700 post-response pairs where the responder gender is tagged.

Overall, if I only use the ones that were tagged for gender of both poster and responder, we are looking at about 450,000 post-response pairs (further examination to be continued).

Additionally, some files contain names of posters rather than their genders. This could be interesting to look at as well:
 - Facebook posts and responses: There are two different categories of Facebook files. This needs to be further examined, but I believe one of the post/response pairs contains the names of the poster, where gender could be inferred.
 - TED posts and responses: Similarly, these files contain the names of the responder.

## Analysis

