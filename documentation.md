## Dataset contents

### SAHtweets.csv
- 6,474,050 items
- Each item represents a tweet including "#StopAsianHate" and its metadata
- The dataset covers the timeframe of January 1, 2020 to December 31, 2022
- For each item, there are 28 features representing the tweet, tweet and user metadata at the time of data collection (early March 2023), and automatic translations of tweets/user bios identified as non-English. The features are as follows:
	1. "id": the unique identifier of the tweet
	1. "lang": language of the tweet, as detected by Twitter; returned as a BCP47 language tag or "und" if no language could be detected
	1. "author\_id": the unique identifier of the user who posted this tweet
	1. "text": the actual UTF-8 text of the tweet
	1. "conversation\_id": the tweet ID of the original tweet of the conversation (which includes direct replies, replies of replies)
	1. "in\_reply\_to\_user\_id": if the tweet is a reply, this field will contain the original tweet's author ID; otherwise, this field will be empty
	1. "username": the Twitter screen name, handle, or alias that this user identifies themselves with; usernames are unique but subject to change; typically a maximum of 15 characters long, but some historical accounts may exist with longer names
	1. "description": the text of this user's profile description (also known as bio), if the user provided one
	1. "location": the location specified in the user's profile, if the user provided one
	1. "verified": indicates if this user is a verified Twitter user ("True") or not ("False") 
	1. "name": the name of the user, if they've defined it on their profile
	1. "public\_metrics.followers\_count": the number of users who follow this user 
	1. "public\_metrics.following\_count": the number of users this user is following 
	1. "public\_metrics.tweet\_count": the number of tweets posted by this user
	1. "public\_metrics.listed\_count": the number of lists that include this user
	1. "created\_date": creation date of the tweet 
	1. "repost\_id": if this tweet is a retweet, quoted tweet, or reply, this field will contain the tweet ID that this tweet is referencing; otherwise, this field will be empty
	1. "retweeted": indicates if this tweet is a retweet ("retweeted"), quoted tweet ("quoted"), or reply ("replied_to"); otherwise, this field will be empty
	1. "mentions": other Twitter users mentioned in the text of the tweet; if none, this field will be empty
	1. "reply\_count": the number of times this tweet has been replied to
	1. "urls": URLs included in the text of the tweet; if none, this field will be empty
	1. "retweet\_count": the number of times this tweet has been retweeted
	1. "hashtags": hashtags included in the text of the tweet; if none, this field will be empty
	1. "like\_count": the number of times this tweet has been liked
	1. "quote\_count": the number of times this tweet has been quoted
	1. "text\_replace\_url": the text of the tweet, with usernames (from mentions) and URLs removed
	1. "translated\_text": if Twitter has identified this tweet as non-English (i.e. not "en", "und", "qme", or "qht"), this field will contain the tweet translated into English via Google Translate; otherwise, this field will be empty
	1. "translated\_description": if Twitter has identified this tweet as non-English (i.e. not "en", "und", "qme", or "qht"), this field will contain the user bio translated into English via Google Translate; otherwise, this field will be empty
- There are 63 total languages in the dataset, as identified by Twitter. Each language and the number of tweets in the language are as follows:
	- English: 3,365,254
	- Thai: 1,318,449
	- "qme" (media links only): 857,242
	- Spanish: 260,532
	- "qht" (hashtags only): 206,689
	- Korean: 100,592
	- Portuguese: 76,685
	- Japanese: 57,905
	- Indonesian: 46,587
	- "und": 45,903
	- French: 24,231
	- Turkish: 22,301
	- Persian: 19,597
	- Vietnamese: 12,929
	- German: 10,636
	- Tagalog: 9,886
	- Arabic: 6,363
	- Russian: 6,330
	- Polish: 5,353
	- Italian: 5,210
	- Chinese: 1,279
	- Catalan: 1,279
	- Dutch: 1,277
	- Estonian: 1,267
	- Sorani Kurdish: 1,132
	- Hindi: 931
	- Romanian: 675 
	- Welsh: 614
	- Haitian Creole: 555
	- Finnish: 349
	- Danish: 298
	- Norwegian: 286
	- Czech: 236
	- Swedish: 226
	- Urdu: 225
	- Basque: 210
	- Lithuanian: 174
	- Hungarian: 152
	- Greek: 119
	- Ukrainian: 87
	- Latvian: 70
	- Khmer: 38
	- Icelandic: 34
	- Slovenian: 32
	- Nepali: 30
	- Tamil: 17
	- Hebrew: 17
	- Lao: 11
	- Bengali: 11
	- Panjabi: 9
	- Malayalam: 8
	- Georgian: 8
	- Sinhala: 7
	- Burmese: 7
	- Marathi: 7
	- Bulgarian: 6
	- Amharic: 5
	- Armenian: 4
	- Sindhi: 3
	- Pashto: 1
	- Serbian: 1
	- Telugu: 1
	- Kannada: 1

### eng\_topics.tsv
- 30 items
- Each item represents a cluster of novel English tweets (i.e. topic) in the SAH dataset
- For each item, there are 7 features representing the cluster. The features are as follows:
	1. "hierarchical\_binary\_repr": the binary representation of the cluster centroid's position in the dendrogram
	1. "tweet\_count": the number of tweets in the cluster
	1. "mean\_timestamp": the mean timestamp of all tweets in the cluster
	1. "std\_time": the timestamp standard deviation (in days) of all tweets in the cluster
	1. "top\_words": a list of the 20 top unigrams, chosen by identifying the 100 unigrams in the cluster closest to the centroid and then, from these 100 unigrams, identifying the 20 most frequent unigrams
	1. "closest\_tweets": a numbered list of the 10 tweets in the cluster closest to the centroid; also included are the posting user's username and, at the end of the tweet in parantheses, the tweet's cosine similarity with the centroid
	1. "topic\_label": the topic label for the cluster (see the associated paper for more details on how the labels were identified)
- There are 10 possible topic labels, as listed below; topics 1-9 can be found in the English subset
	1. AAPI Heritage Month
	1. Solidarity with AAPI community
	1. Advocating action and awareness
	1. Anti-Asian hate crimes
	1. SAH statement 
	1. Commodification of SAH
	1. COVID-related misinformation/stigma
	1. Connection with BLM
	1. BTS/ARMY
	1. Unidentified

### eng\_users.tsv
- 100 items
- Each item represents a cluster of user bios from users who posted at least one English tweet in the SAH dataset
- For each item, there are 9 features representing the cluster. The features are as follows:
	1. "hierarchical\_binary\_repr": the binary representation of the cluster centroid's position in the dendrogram
	1. "bio\_count": the number of bios in the cluster
	1. "mean\_timestamp": the mean timestamp of the first tweet associated with each bio in the cluster
	1. "std\_time": the timestamp standard deviation (in days) of the first tweet associated with each bio in the cluster
	1. "twts\_per\_user": the average number of tweets posted in the dataset per user, by users in the cluster
	1. "nt\_to\_rt": the ratio of novel tweets to retweets/quote-tweets/replies posted in the dataset by users in the cluster (i.e. number of novel tweets divided by number of retweets/quote-tweets/replies)
	1. "top\_words": a list of the 20 top unigrams, chosen by identifying the 100 unigrams in the cluster closest to the centroid and then, from these 100 unigrams, identifying the 20 most frequent unigrams
	1. "closest\_bios": a numbered list of the 10 bios in the cluster closest to the centroid; also included is the user's username
	1. "user\_group\_label": the final user group label for the cluster (see the associated paper for more details on how the labels were identified)
- There are 8 possible user group labels, as listed below; all 8 can be found in the English subset
	1. K-pop fan
	1. Political affiliation in bio
	1. Activist
	1. East/Southeast Asian identity
	1. National identity (non-Asian)
	1. Job
	1. Generic identity marker (i.e. pronouns, astrological sign, age, location, quote, familial role, hobbies, religious identity)
	1. Unidentifiable

### noneng\_topics.tsv
- 30 items
- Each item represents a cluster of novel non-English tweets (i.e. topic) in the SAH dataset
- For each item, there are 8 features representing the cluster. The features are as follows:
	1. "hierarchical\_binary\_repr": the binary representation of the cluster centroid's position in the dendrogram
	1. "tweet\_count": the number of tweets in the cluster
	1. "mean\_timestamp": the mean timestamp of all tweets in the cluster
	1. "std\_time": the timestamp standard deviation (in days) of all tweets in the cluster
	1. "top\_lang": the three most frequent languages in the cluster, with the number of tweets in that language and the corresponding percentage of the cluster in parantheses
	1. "top\_words": a list of the 20 top unigrams, chosen by identifying the 100 unigrams in the cluster closest to the centroid and then, from these 100 unigrams, identifying the 20 most frequent unigrams
	1. "closest\_tweets": a numbered list of the 10 tweets in the cluster closest to the centroid; also included are the posting user's username and, at the end of the tweet in parantheses, the tweet's cosine similarity with the centroid
	1. "topic\_label": the topic label for the cluster (see the associated paper for more details on how the labels were identified)
- There are 10 possible topic labels, as listed below; topics 3, 4, 5, 7, 9, and 10 can be found in the non-English subset
	1. AAPI Heritage Month
	1. Solidarity with AAPI community
	1. Advocating action and awareness
	1. Anti-Asian hate crimes
	1. SAH statement 
	1. Commodification of SAH
	1. COVID-related misinformation/stigma
	1. Connection with BLM
	1. BTS/ARMY
	1. Unidentified

### noneng\_users.tsv
- 75 items
- Each item represents a cluster of user bios from users who posted at least one non-English tweet in the SAH dataset
- For each item, there are 10 features representing the cluster. The features are as follows:
	1. "hierarchical\_binary\_repr": the binary representation of the cluster centroid's position in the dendrogram
	1. "bio\_count": the number of bios in the cluster
	1. "mean\_timestamp": the mean timestamp of the first tweet associated with each bio in the cluster
	1. "std\_time": the timestamp standard deviation (in days) of the first tweet associated with each bio in the cluster
	1. "twts\_per\_user": the average number of tweets posted in the dataset per user, by users in the cluster
	1. "nt\_to\_rt": the ratio of novel tweets to retweets/quote-tweets/replies posted in the dataset by users in the cluster (i.e. number of novel tweets divided by number of retweets/quote-tweets/replies)
	1. "top\_words": a list of the 20 top unigrams, chosen by identifying the 100 unigrams in the cluster closest to the centroid and then, from these 100 unigrams, identifying the 20 most frequent unigrams
	1. "top\_location": a list of the 10 most frequent unigrams from the "location" field of users' profiles in the cluster; pronoun-related unigrams were excluded from this list
	1. "closest\_bios": a numbered list of the 10 bios in the cluster closest to the centroid; also included is the user's username
	1. "user\_group\_label": the final user group label for the cluster (see the associated paper for more details on how the labels were identified)
- There are 8 possible user group labels, as listed below; user groups 1, 3, 4, 5, 6, 7, and 8 can be found in the non-English subset
	1. K-pop fan
	1. Political affiliation in bio
	1. Activist
	1. East/Southeast Asian identity
	1. National identity (non-Asian)
	1. Job
	1. Generic identity marker (i.e. pronouns, astrological sign, age, location, quote, familial role, hobbies, religious identity)
	1. Unidentifiable


