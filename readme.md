# Twitter HOPE Data Structure
A brief introduction to the data structure for the HOPE project



## Folder Structure
Located on Grundtvig on: `/data`
```
twitter_hope_001
├── raw
│   ├── rehydration DATE
│   │   ├── readme.md
│   │   └── ...
│   ├── rehydration DATE
│   ├── ...
│   ├── subdatafolders
│   │   ├── readme.md
│   │   └── ...
└── preproccessed
│   ├── da
│   │   ├── tweet_id.txt
│   │   ├── td_DATE_da_tlpdsn_001.ndjson
│   │   └── ...
│   ├── en
│   │   └── ...
│   ├── no
│   │   └── ...
│   ├── ...
...
```
`001` denote the project ID.
Ideally, all folders should use lowercase and be split by `_`.

## Raw Data
Raw data can be found in the `raw` folder and includes folders directly from the scrape. These include two categories, initial scrape (including historic data) and rehydration. Each folder is intended to include data from the scrape as well as a markdown (`readme.md`) on how the data was collected.

## Preprocessed Data
The preprocessed data can be found in `preprocessed` and contains a folder for each language. Each of these folders contains a `.txt` file containing all the tweets ids (`tweet_id_001.txt`) and preprocessed Twitter data. The Twitter data is in the following format:

```td_{DATE}_{LANG}_{PREPROCESSING FLAGS}_{ID}.ndjson```

Where;
- `td` stand for Twitter Data
- `DATE` is the date the tweets in the file is from
- `PREPROCESSING FLAGS` is denotes what preprocessing have been applied to the data
- `LANG` is the language the tweets are believed to contain (or at least should be processed as)
  - `h`: Historic/purchased data tag
  - `t`: Tokenization
  - `l`: Lemmatization
  - `p`: POS-tags
  - `d`: Dependency Parsing
  - `s`: Sentiment Analysis
  - `n`: Named Entity Recognition  
- `ID`: project id, 001 for HOPE


## Intended pipeline
- Data comes into the raw folder with a `readme.md` describing the scrape method (or is added to its respective scrape)
- Raw data is sorted into preprocessed by:
  - sorting into specific languages (currently using twitters flag)
  - standardizing to .ndjson files (e.g. .tsv's from the TCAT scrape is transformed to .ndjson)
- Preprocessing tags is added one or multiple at a times and the replacing the file with its respective tag.


