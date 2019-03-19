# Progress Report

## Preliminary Report (2/7/19)
I created my GitHub repository, wrote a quick README document, and published the project plan. I have a large data set that will work well with my project ideas, and have examined it enough to start gathering ideas on how to clean it up. I also started searching for/thinking about what kind of articles I should read up on for the sociolinguistics aspect.

## First Progress Report (2/21/19)
### Data Acquisition and Preliminary Examination
At this point, I have confirmed that the dataset I've been working with (RtGender) is the one I definitely want to use. It is fairly large and contains a lot of information, but is also manageable to handle. Data samples can be found [here](data_samples/). I was a little unsure of the extent to which I should post the data samples. I decided to use 500 lines from the Facebook congress posts and 500 lines from the Reddit responses, but this can be modified/updated if needed.

I then moved on to examining the dataset to get a better idea of what I am able to do with it. There are 10 csv files, which I examined closely in my [exploratory data analysis - exploring the dataset](exploratory_data_analysis/exploring_dataset.ipynb). Additionally, I can pretty confidently say that I won't be using the annotations file (examined at the end of the linked file), as it doesn't directly relate to my goals for the project.

I've also been reading up on some aspects of sociolinguistics, though not very much. This is something I want to focus more heavily on soon as I begin to develop more formal hypotheses.

### Cleaning/Reorganizing Data
While exploring the data set, I was able to make some decisions about how I want to alter the data set to fit my own needs. The most important goal for my modifications was to combine the post and response files so that we could see them at the same time, rather than matching up the response to the specific post in another DataFrame. However, I don't think I will be combining all of the data sets - that is, I will keep the different categories separate (Facebook congress, Facebook wiki, Fitocracy, Reddit, and TED). The beginning of my cleaning and reorganizing can be found in my [exploratory data analysis - modifying the dataset](exploratory_data_analysis/modifying_dataset.ipynb).

### Sharing Plan
Included on the website where I downloaded my data from is some (very brief) licensing information:

> RtGender is available for research purposes only. By downloading the corpus you agree that you will use it only for non-commercial, non-nefarious research purposes.
>
> Sign your name to agree that you are downloading the corpus for research purposes only.

I still have to read up on this a bit, as I'm not entirely sure what this means for redistribution of the data. Am I allowed to redistribute it freely, as long as it's for non-commercial research purposes? There is also contact information listed, so if it comes down to it, I can ask the creators directly. I think that overall, the sharing of the data shouldn't be too difficult as long as they are credited.

However, I don't know if it's reasonable to share all 5 GB of my data (even if it is permitted). At the minimum, I would like to be able to display some data from each file, so the format of the different files is clear.

## Second Progress Report (3/19/19)
### Moving Forward with the Data
My biggest accomplishment for this progress report is probably found in finishing up my data reorganization. I created and combined dataframes for posts and responses for all of my files. This can be found in the same modification file that I started in the first progress report, which is found [here](exploratory_data_analysis/modifying_dataset.ipynb). In the file, I walk through the process of how I combined these files and made them my own. I also pickled the files so I could reopen them in a new Jupyter Notebook file dedicated to more in-depth analysis.

Moving on to some more formal analysis can be found [here](exploratory_data_analysis/main_analysis.ipynb). In this file, I reiterate some basic analysis of the files to keep it all in one place, as well as delving a little deeper. I then began to move on to conduct some basic linguistic analysis, and have so far completed the token count and average sentence length. However, since my files are so large, I conducted this analysis on a much smaller sample.

### Data Size
I am using 5 files: Facebook Congress posts, Facebook Wiki posts, Fitocracy posts, Reddit posts, and TED posts. These are each made up of posts and their corresponding responses (except for the TED file - this only has responses as the original source was a video and not a post). I have them organized so that each response has it's own row, since many times there are multiple responses per post. When this happens, the info about the post is repeated in each row, but the info about the response is unique to that row. The actual sizes are:

- Facebook Congress: 14,015,811 entries
- Facebook Wiki: 10,699,137 entries
- Fitocracy: 318,535 entries
- Reddit: 1,453,512 entries
- TED: 190,347 entries

For my linguistic analysis, I have reduced the size of each of these files to 50,000 entries, since any sort of analysis on files this big seemed to be going very slowly.

### Sharing Scheme
The data seems to be limited to only those who sign to agree to use it for non-commercial use. Thus, I should not be able to redistribute this data, as I don't know what other people may do with this data. It can be downloaded for anyone who wants to use it though, as long as they personally sign their name. Downloading is located at the bottom of [this page](https://nlp.stanford.edu/robvoigt/rtgender/).

### Licensing
I am including an MIT license with my project. This is because I don't mind others using and redistributing my code, as long as I am credited as the original code source. I know that there are still many improvements that can be made to my analysis, and it would definitely be easier for others to do so when it's organized in the way that I have put the data together. I'm very open to seeing how other people could use and develop my analysis. It's also important to note that if they want to recreate my code exactly, they still have to sign for the data from the original data source.

## Third Progress Report (4/9/19)