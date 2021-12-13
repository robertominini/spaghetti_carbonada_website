# Chilling Effect Explained - Analyzing Other Causes of Wikipedia Views Changes in the Context of World Historical Events

## Abstract

In the original *Chilling Effects* paper, the authors decided to remove *Hamas* from the set of analized topics, due to the ongoing conflict in the Middle East which was causing the values of average views per month to skyrocket. This action highlights two weaknesses of the author’s analysis. First, the average score might be dominated by the trends of a single, highly popular wikipedia page from the selected set. Second, there might be more highly significant historical events which affected the analysis by generating increased traffic to the pages related to the event.  
In this work, we will make an effort to improve the analysis and address the aforementioned problems using the original data and the Google Trends from the related timespan. We will then reproduce the analysis on the new data to show whether the phenomenon described in the paper can be still observable with statistically significant confidence.

## Research questions

* How big is the importance of each separate article trend on the original paper results?
* How important was the influence of the external events on the weekly wikipedia views?  
External events are illustrated by huge spikes in the google trends dataset. To recognize them, we compute the derivative of the weekly interest score, and find the weeks where the derivative is more than the mean + 4 std. We choose this value, as this is the approximate height of the max peak of derivative in the only article, which the authors of the original dataset decided to treat as an outlier (hamas)
* Is the original paper's result still relevant if we reduce the impact of "breaking news" and topic popularity disproportion in the original data, as such can the results be reproduced using a more general data set, such as Google Trends?  
Google Trends is more sensitive to world events which is why it is interesting to use this dataset to detect any other outlier there could be - it might have been decisive, but not visible enough in the wikipedia data as we expect the breaking news to spike much higher than the related wikipedia articles  
The only kind of outliers we'll consider are spikes caused by external events. We don't have any missing data in our dataset as we re-gathered the views for the missing months.

## Proposed dataset

In addition to using the original wikipedia dataset provided by TA, (with re-downloaded two last months), we propose a set of Google Trends queries (Google Trends) to identify the trends of each of the 48 topics used in the original paper during the same timespan as the wikipedia views data.  
Google Trends dataset is interesting because it uses a (random) sample of the queries in the google search bar, which is more general than just analysing the wikipedia views. So if there were a chilling effect, people would be chilled from searching a specific word, before even clicking on the wikipedia article. And generally, for events and news, people are looking things up in google, and only after click on the wikipedia article directly from the search engine. Google trends allows us to explore the magnitude of trends in searches, in a scale from 0 to 100. It illustrates the interest as a proportion of all searches on all topics on Google at that time and location (https://medium.com/google-news-lab/what-is-google-trends-data-and-what-does-it-mean-b48f07342ee8). It is easy to download the data we want with the button ‘Download’. We get a csv file with two columns : the week and the interest on the 0-100 scale from the wanted keyword. We would do that for all of our subjects.  
Because the values provided by Google Trends are their own popularity metrics scaled from 0 to 100, we cannot use it easily for quantitative analysis. However, we can identify sharp spikes in interest which correspond to the news - eg. when querying for "terrorism", we can see a massive spike, 50 points higher from the second highest point, around a week of 14-20.04.2013. The query reveals that the spike is related to the Boston Marathon Bombing of 15.04.2013, an important event which could have affected the wikipedia views as well, and that was not counted as an outlier in the study. We can also plot the regression analysis and compare the results for the two datasets.

## Methods

### A: Analyse Google Trends for the paper keywords

1) Gather the data from Google Trends using google API, separately for every article in the 30 terrorism-related article set
2) Identify the sharp spikes in the Google Trends data. 
3) Use google search to recover the related  "disturbing" event from the world news. 
4) Plot the original wikipedia views data topic-by-topic to identify their trends and compare them against the Google Trends data.  
Our final analysis result will be the same regression analysis approach as used in the original paper. We'll then compare this result with the results of the authors, to see whether after our amendments the trend is still as clear as before.

### B: First modified reproduction

1) Try to deal with the problem of different topics having different numbers of views by re-scaling these numbers. See our first question for the TA’s about this.
2) Try to treat the views data which was affected by "historical spike". Again we have some ideas on how to do that, see the questions’ section.

### C: Second modified reproduction

1) Plot the whole dataset once more and see whether the trend observed by the paper's authors is still visible.

## Proposed timeline

* 27.11 - 10.12 : Code  
Data wrangling : 10%  
Visualisation : 30%  
Drawing conclusions and proving them statistically : 60%
* 11.12 - 18.12 : report and video preparation

## Organization within the team

### 27.11 : preparation and upload of P4 notes

* All the team

### 30.11 : data acquisition scripts ready (start step A)

* Elisa will write scraping script for all the 48 csv from Google Trends
* Michał will prepare the data from Wikipedia
* Eva will calculate statistics from the two datasets to put in our report

### 05.12 : plots for each topic, discussion on findings (finish step A and start B)

* Elisa will identify the spikes from the Google Trends dataset and search related breaking news
* Michał will plot wikipedia data topic by topic against google trends data
* Eva will normalize the data from wikipedia
* All the team will discuss the results

### 07.12 : treat outliers (finish step B)

* All the team will discuss on how to treat outliers
* One of them will do it
* The other two will compute statistical tests in order to draw conclusions

### 11.12 : code is ready with calculated stats, starting the report

* Elisa will write : abstract, introduction, related work, (brief) data collection
* Eva will write : dataset description with summary statistics, methods with math and description of main algorithms
* Michał will write : results and findings, conclusions

## Questions for TAs (it's clear now, thanks!)

1) When we want to normalize wikipedia views for all articles, we thought of multiple ways to do it, and don’t know which one is the most relevant for this. We could normalize the views so that each article has the same importance over the whole time period. We could also do that for each day, we compute each fraction of the article views. Maybe we should try both and see what’s better?

2) When we identify the outlier days, should we drop the topic as an outlier, or filling up the "historical" months data by arbitrary value ? (mean of neighbors? mean over all period without this date? mean of before june 2013 if the outlier is before or mean of after june 2013 if the outlier is after?). Also, we could of course try each possibility.

3) We wonder whether calculating correlation between the two types of data seem reasonable. If yes, we wonder whether it'll be worthwhile to fit the lines of the google trends to the lines of the separate topic views to show the trends similarities and differences.
