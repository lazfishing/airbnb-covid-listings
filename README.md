# Analyzing Airbnb Listing Descriptions

*How did Airbnb owners adapt their listing descriptions to COVID-19?*

The Airbnb market was significantly affected by the COVID-19 travel/lockdown restrictions in NYC starting March 2020. Our motivation was to understand the extent of damage to the NYC Airbnb market, on both demand and supply-sides. Interestingly, we found that a simple Word2Vec model can be used to efficiently infer consumer preferences and concerns. Real-time implementation could potentially help stakeholders anticipate structural changes in the housing rental market.

## Data

Airbnb (1) Listings and (2) Review datasets for NYC from 1st January 2018 to 11th October 2020 were downloaded from http://insideairbnb.com/.

## Results

Listing descriptions were tokenized and a simple Word2Vec model was used to create word embeddings. Using cosine similarity to measure semantic distance, the *n* most similar tokens to each word could be found. For example, the 10 most similar words to `coronavirus` were:

```
['pandemic', 'covid', 'outbreak', 'precautions', 'crisis', 'virus', 'sanitizing', 'viral', 'cdc', 'procedures']
```

We can visualize these embeddings in 2D space.

![t-sne visualization of coronavirus-related keywords](/images/tsne_word2vec.png)

Using these semantically similar keywords, we were able to increase the sensitivity of our analysis (i.e., we can pick up more instances of listings containing a group of pandemic-related keywords as opposed to a single keyword like 'coronavirus'). Aggregated by month, we notice a sharp increase in pandemic-related keywords peaking in July 2020:

![keyword frequency](/images/wordfreq.png)

Similarly, the percentage of listings that contained these pandemic-related keywords increased after lockdown restrictions were imposed in NYC as more Airbnb owners reacted to regulatory/supply-side changes in the housing rental market.

![frequency of listings containing keywords](/images/listingfreq.png)
