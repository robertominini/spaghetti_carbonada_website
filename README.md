# Title: “Analyzing US Politicians Lexical Level” 

## Abstract:
In recent years we often get the feeling that the level of the political debate has been quickly degrading. There seems to be a tendency, especially from populist candidates to propose extremely simplified solutions to complex problems. This is reflected in the ways politicians communicate with the public. Watching US presidential elections’ debates, as well as similar ones between Italian politicians, analysts noticed the significant difference in the complexity of the language used by the two sides. It’s often populist politicians using less refined language, very similar to spoken language, with a restricted use of vocabulary. The goal of this analysis is to apply an analytical methodology to this matter by scoring quotes by US politicians’ on a lexical diversity basis as well as complexity, using Flesch–Kincaid and MTLD measures. Finally we will compare aggregated scores by prominent figures of US politics and multiple sets of politicians grouped by affiliation, etc. 

## Motivation and data story:
With this analysis we want to understand if there are significant differences in terms of complexity and refinement in the use of English by different groups of US politicians. Watching Trump’s presidential debates in 2016 and 2020 as well as a similar confrontation between two Italian politicians sparked various discussions regarding the lexical level of the people involved. Many analysts underlined to what extent speech complexity differs between candidates which are often referred-to as populists and more moderate ones. Linguists highlighted how basic the vocabulary and grammar structures used by Trump are.
The goal of this analysis is to use the Quotebank database to extend this analysis of the linguistic level of specific individuals to a broader group of people, US politicians. We aim to use an analytical approach, in the pursuit to draw grounded conclusions on traits of the language used. The idea is to extract quotes attributed to US politicians and, after some data cleaning, measure lexical features of the quotes such as vocabulary amplitude and refinement, avg. sentence length and others to be combined inside readability scores. Plus, we could gather the most frequent words used by politicians and analyze to which context (formal or spoken language) they belong, using the COCA dataset to compute the relative frequency of each word in different contexts.  
Finally, we want to present the findings, drawing interesting comparisons both between prominent individual politicians as well as relevant groups of Senators and Congressmen. We aim to present insights on the level of english of politicians grouped by party affiliation, electoral district or State, political post, schooling level and others. The question we are asking is then, are there significant differences between these groups. 

## Research questions:
- Is there any significant difference in terms of language complexity and refinement between the last two presidential candidates, Trump and Biden?
- What are their most used words? Do they use more words belonging to formal or spoken vocabulary?
- Is it possible to spot similar differences between wider ranges of politicians? For example what can we say comparing Republicans and Democrats? We would like to create a clear map of the level of lexic used by politicians from various states or with different levels of experience, etc. 

## Additional datasets:
- integrate Wikidata dumps, to select quotes from US politicians and filter them by groups.
- We ideally would like to use Text Inspector APIs to analyze the quotes, these APIs use Carnegie Mellon dictionary to compute the Flesch-Kincaid Grade level, type/token ratio and other interesting metrics (we are waiting to be granted access to the API)
- Corpus of Contemporary American English (COCA) from english-corpora.org to score words based on how likely they are to be used in a formal vs spoken context

## Methods:
- NLTK library’s tokenizer to clean quotes and prepare them to be scored.  
- Text Inspector APIs to get measures of the language used.
- Creation of additional metrics of polishness of language using the relative frequency of words in different contextes. 
- Plotly to create interactive plots and maps.

## Proposed timeline:
- First 2 weeks
Load and clean data
Integrate wiki-data, extract features for each author and create subsets of the dataset useful for following analysis.
Apply NLTK or Text Inspector tools to tokenize the quotes
Obtain Text Inspector’s APIs access and implement the methods to our dataset
From each quote compute lexical complexity measures
For each author aggregate quotes score and compute author’s scores.
- Third week:
Pairwise comparison of interest: filter prominent politicians, compare scores, collect most used words by each and analyse to which linguistic register they belong to (formal or spoken)
Aggregate data over subgroups (see research questions)
- Last 2 weeks:
Create interactive visualizations 
Create data story
Draw conclusions

## Organization within the team:
We will be working in pairs splitting each of the 3 sections described in the timeline. 
First 2 weeks: one group will focus on cleaning the data and integrate the additional datasets while the other two will focus on the implementation of external libraries, tokenize pipeline and APIs.
Third week: One group will focus on additional metrics for the paiwise analyses, while the other will work to aggregate data for various subests.
Last 2 weeks: one group will focus on creating interactive visualization of the data while the other will create and comment the data story. Final reviews will be made together.

## Questions for TAs:
- How to deal with multiple QIDs? our apporach (remove those >3 homonyms and assume quotes from those with less are from the politician) is ok? what would you suggest? In the future we could try to integrate with the relevance of the web page and select the quote iff the relative relevance of the politician’s wiki page is high enough = low risk of an homonym being quoted.
- are the research questions interesting enough? would you suggest any additional analysis?
- How can we safely identify which is the last party among the list of parties in the speaker attributes dataset?
