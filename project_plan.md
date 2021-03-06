# Gendered Interaction Online: Project Plan

## Goals for the project
I have two main goals for my project (and a potential third, although somewhat doubtful about it):

1. Look at GENDER X GENDER
2. Predictive analysis: guess gender of poster and gender of responder
3. (?) Still unsure if I want to do anything with the sentiment file

More details can be found in the analysis section below.

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

 - Facebook posts and responses: There are two different categories of Facebook files. This needs to be further examined, but I believe one of the post/response pairs contains the names of the poster, where gender could then be inferred by examining the names.
 - TED posts and responses: Similarly, these files contain the names of the responder, and gender could be inferred.

## Analysis

### GENDER x GENDER linguistic analysis
To start, I want to look at some simple linguistic analysis measures. First, I can examine language used by male vs. female, ignoring the poster vs. responder category. This is useful to just confirm typical language use of different genders.

I then want to move on the a GENDER x GENDER analysis, which can be summarized in the below table:

|                   | Male responder | Female responder |
|-------------------|----------------|------------------|
| **Male poster**   | MALE x MALE    | MALE x FEMALE    |
| **Female poster** | FEMALE x MALE  | FEMALE x FEMALE  |

Essentially, I want to examine how interactions differ when a male is responding to a male vs. a female and a female is reponding to a male vs. a female. A more formal hypothesis about how these differ can be generated after I read up on more sociolinguistic papers.

### Predictive analysis
As I don't really have specific training, development, and testing data sets, this analysis would not be that formal. However, I would like to be able to implement some sort of machine learning to identify the gender of the poster and/or responder. There are two different ways I am thinking of looking at this:

1. Predict gender just based off of the post, regardless of if they are the original poster or the responder.
2. If results from GENDER x GENDER analysis are significant (i.e., if I find that male responders respond differently if they are responding to a male vs. a female, and vice versa), it would be interesting to try to predict what gender they are responding to, given the responder's gender and the substance of their post. For this, I could train on the files that contain the gender of the responder, and do testing on the files that contain the name of the responder (in the Facebook and/or TED files). Though I'm not aware of the actual gender, looking at the names of the responders that were tagged as male vs. female could give some insight on how accurate my predictive analysis is.

Lastly, there is a file tagged for sentiment. I could train on this as well, and then develop and/or test on any of the other files in the data set, as they are not tagged for sentiment. However, I'm not sure if this is as relevant to my main goal of the project.