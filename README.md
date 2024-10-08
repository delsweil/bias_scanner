This repository contains three tables in the form of csv files. The primary key is ‘url’

The list of pages is originally sourced from the search result pages of a user study published in Nature:

Aslett, K., Sanderson, Z., Godel, W., Persily, N., Nagler, J., & Tucker, J. A. (2024). Online searches to evaluate misinformation can increase its perceived veracity. Nature, 625(7995), 548-556.

The original dataset(s) can be found here: https://github.com/SMAPPNYU/Do_Your_Own_Research

Each url that was still online and processable was passed to https://biasscanner.org/ using their trained model and suggested prompt. Many of the pages, but not all are news articles. We only include pages where there is a newsguard score available for the page’s domain.

The input and output are stored in the files overall_bias.csv, sentences.csv and article_content.csv

overall_bias.csv has the following columns with one row per page processed:

"url”: the url of the page passed                        
"total_sentence_count”: the number of sentences in the raw text passed to the model (using quanteda package in R)
"num_biased_sentences”: as returned by the model      "average_bias_strength”: the arithmetic mean of the bias_strength for all of the sentences classified as biased by the model
"biased_sentence_percentage": the percentage of sentences for the text classified by the model to be biased
"conclusion”: the free text explanation of the overall impression of the text as provided by the model                "domain": the top-level domain of the page e.g. guardian.co.uk
"newsguard" : the newsguard (https://www.newsguardtech.com/) score for this domain as extracted from the Aslett et al. data.

sentences.csv has the following columns with one row per sentence determined by the model to be biased:

"text”: the raw sentence text
"bias_type”: the type of bias assigned by the model
"bias_strength”: the strength of the biased as assigned by the model
"bias_description”: the textual explanation provided by the model "url”: the url of the page from which the sentence was sourced


article_content.csv has the following columns with one row per page processed 
"url": the url of the page processed
"title": the title extracted (using the rvent package in R)
"body": the body of the extracted page (using the rvent package in R)
