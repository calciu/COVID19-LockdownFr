# LockdownDay (#ConfinementJour) COVID-19-TweetIDs

For the associated research paper see https://arxiv.org/ftp/arxiv/papers/2005/2005.05075.pdf


This repository contains an ongoing collection of tweets IDs associated with the lockdown period due to the coronavirus COVID-19 (SARS-CoV-2), that started in France on March 17, 2020. 

We used the Twitter’s search API to gather on a daily basis Tweets defined by  hashtags #confinementJour1 to #confinementJour_n (that is LockdownDay1 to n).

To comply with Twitter’s [Terms of Service](https://developer.twitter.com/en/developer-terms/agreement-and-policy), we are only publicly releasing the Tweet IDs of the collected Tweets. The data is released for non-commercial research use. 

Additionally we release annotations of this corpus using sentiment and emotions mesurement instruments. This allows researchers to evaluate the capability of these tools to capture variations of émotions expressed by people on a daily basis.

The associated paper to this repository can be found here: [#COVID-19: The First French COVID19 Lockdown Twitter Dataset](under development)

## Data Organization
### Tweet Sentiment and Emotion Annotations Files
Sentiment and Emotion Annotations files (in .csv format) are available in the LockdownAnnot folder. Their names have the following pattern dff_method_numberOfDays_chunk.csv (dff meaning data frame free and the method is nrc or lds). In order to facilitate comparisons we added the French language tweets of a bigger dataset (available at https://github.com/echen102/COVID-19-TweetIDs) of which we have hydrated the months 1 to 4. Therefor their names end with *1-4fr.csv 


#### dff\_nrc\_55\_1.csv 
nrc files contain ten columns the first eight represent emotions frequencies and the last two sentiments frequencies per tweet

| anger | anticipation | disgust | fear | joy | sadness | surprise | trust | negative | positive |
| ----: | -----------: | ------: | ---: | --: | ------: | -------: | ----: | -------: | -------: |
|     0 |            0 |       0 |    0 |   0 |       0 |        0 |     0 |        0 |        0 |
|     0 |            0 |       0 |    1 |   0 |       0 |        1 |     0 |        3 |        0 |
|     1 |            1 |       0 |    2 |   1 |       1 |        1 |     4 |        2 |        2 |
|     0 |            1 |       0 |    2 |   0 |       1 |        0 |     0 |        1 |        0 |

#### dff\_lds\_55\_1.csv 
lds files contain four columns negative and positive sentiment frequencie, number of words and identification number of the tweets
    
| Neg\_lsdfr | Pos\_lsdfr | nb | id |
| ---------: | ---------: | -: | -: |
|          0 |          0 |  1 |  1 |
|          0 |          0 | 20 |  2 |
|          0 |          1 | 38 |  3 |
|          1 |          1 | 26 |  4 |


#### dff\_emos\_55\_1.csv
emos files contain five columns. The first is a list of emojis separated by ";", the second indicates the number of emojis per tweet. The other three indicate the minimum, average and maximum sentiment score (on a scale from -1 to 1) 


| emoji  | nemoji | min\_sentsc | mean\_sentsc | max\_sentsc |
| :----- | -----: | ----------: | -----------: | ----------: |
| ;      |      0 |          NA |           NA |          NA |
| 😂;😂;😂; |      3 |       0.221 |       0.2210 |       0.221 |
| 📷;     |      1 |       0.430 |       0.4300 |       0.430 |
| 😆;😅;🤣; |      3 |       0.178 |       0.2935 |       0.409 |

### Tweet IDs files

The Tweet-IDs that help recover (hydrate) all collected datasets are organized as follows:
* Tweet-ID files are stored in two folders LockdownDays and LockdownOther. The first has tweets collected with the lockdown day hashtag #ConfinementJourX, the second one contains tweets collected using a larger set of hashtags indicating the lockdown period.
* The file names have the following pattern: a prefix “df_ids” followed by either "jX" indicating the day (jour) for the first folder and by "confX" meaning lockdown (confinement) for the second.

## Notes About the Data
A few notes about this data: 
* We will be continuously maintaining this database for the foreseeable future, and will be uploading new data on a weekly basis.  
* We will keep a running summary of basic statistics as we upload data in each new release. 
* Consider using tools such as the [Hydrator](https://github.com/DocNow/hydrator) and [Twarc](https://github.com/DocNow/twarc) to rehydrate the Tweet IDs. Instructions for both are in the next section. 
* Hydrating may take a while, and Tweets may have been deleted since our initial collection. If that is the case, unfortunately you will not be able to get the deleted Tweets from querying Twitter's API.

## How to Hydrate

### Hydrating using [Hydrator](https://github.com/DocNow/hydrator) (GUI)
Navigate to the [Hydrator github repository](https://github.com/DocNow/hydrator) and follow the instructions for installation in their README. As there are a lot of separate Tweet ID files in this repository, it might be advisable to first merge files from timeframes of interest into a larger file before hydrating the Tweets through the GUI. 

### Hydrating using [Twarc](https://github.com/DocNow/twarc) (CLI)
Many thanks to Ed Summers ([edsu](https://github.com/edsu)) for writing this script that uses [Twarc](https://github.com/DocNow/twarc) to hydrate all Tweet-IDs stored (in their corresponding folders). 

First install Twarc and tqdm
```
pip3 install twarc
pip3 install tqdm
```

Configure Twarc with your Twitter API tokens (note you must [apply](https://developer.twitter.com/en/apply-for-access) for a Twitter developer account first in order to obtain the needed tokens). You can also configure the API tokens in the script, if unable to configure through CLI. 
```
twarc configure
```

Run the script. The hydrated Tweets will be stored in the same folder as the Tweet-ID file, and is saved as a compressed jsonl file
```
python3 hydrate.py
```

# Data Usage Agreement
This dataset is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International Public License ([CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)). By using this dataset, you agree to abide by the stipulations in the license, remain in compliance with Twitter’s [Terms of Service](https://developer.twitter.com/en/developer-terms/agreement-and-policy), and cite the following manuscript: 

Sophie Balech, Christophe Benavent, and Mihai Calciu. 2020. #COVID-19: The First Public COVID19 Containment Twitter Dataset.  arXiv:(under development)

# Statistics Summary (v0.2 55 Lockdown days up to May 11 2020)
Number of Tweets : ** 2598250 **

| ISO | Language  | No. tweets | % total tweets |
| -------: | ------:  | --------: |---------: |
| fr | French  | 2474086 | 95.22 |
| en | English  | 31614 | 1.22 |
| es | Spanish  | 2997 | 0.12 |
| ca | Catalan  | 2412 | 0.09 |
| pt | Portuguese  | 1817 | 0.07 |
| it | Italian  | 1153 | 0.04 |
| ht | Haitian  | 953 | 0.04 |
| ja | Japanese  | 731 | 0.03 |
| tr | Turkish  | 672 | 0.03 |
| in | Indonesian  | 588 | 0.02 |
| de | German  | 505 | 0.02 |
| no | Norvegian  | 345 | 0.01 |
| tl | Tagalog (Philipnes)  | 280 | 0.01 |
| ar | Arabic  | 264 | 0.01 |
| eu | Basque  | 263 | 0.01 |
| ro | Romanian  | 254 | 0.01 |
| nl | Dutch  | 249 | 0.01 |
| et | Estonian  | 245 | 0.01 |
| da | Danish  | 192 | 0.01 |
| sv | Swedish  | 185 | 0.01 |



# Inquiries
If you have technical questions about the data collection, please contact Mihai Calciu at **mihai.calciu[at]univ-lille[dot]fr**.

If you have any further questions about this dataset please contact Christophe Benavent at **christophe.benavent[at]gmail[dot]com**.
