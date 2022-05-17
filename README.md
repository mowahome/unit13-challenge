# Unit13-challenge- The Power of Unsupervised Learning

One of your most important clients, a prominent investment bank, is interested in offering a new cryptocurrencies investment portfolio for its customers, however, they are lost in the immense universe of cryptocurrencies. They ask you to help them make sense of it all by generating a report of what cryptocurrencies are available on the trading market and how they can be grouped using classification.

In this homework assignment, you will put your new unsupervised learning and Amazon SageMaker skills into action by clustering cryptocurrencies and creating plots to present your results.

## Data Preprocessing
I imported data from the csv file and read it into a dataframe. 
I kept only the necessary columns:'CoinName','Algorithm','IsTrading','ProofType','TotalCoinsMined','TotalCoinSupply'.
Kept only the cryptocurrencies that are trading (isTrading=True) and those with a working algorithm (algorithm not equal to N/A).
I removed the nulls and crytocurrencies that had no coins mined.
I created dummy variables for the text features remaining (Algorithm and ProofType). I then used the standardscaler from sklearn to standardize all the data in the text features dataframe.

#### Reducing Data Dimensions Using PCA
I reduced the dimensions of the `X` DataFrame down to three principal components and created a dataframe using the original dataframe index.

#### Clustering Cryptocurrencies Using K-Means
I performed the following tasks:

1. Created an Elbow Curve to find the best value for `k` using the `pcs_df` DataFrame.
see (images folder)

2. Once you define the best value for `k`, run the `Kmeans` algorithm to predict the `k` clusters for the cryptocurrencies data. Use the `pcs_df` to run the `KMeans` algorithm.

3. Create a new DataFrame named `clustered_df`, that includes the following columns `"Algorithm", "ProofType", "TotalCoinsMined", "TotalCoinSupply", "PC 1", "PC 2", "PC 3", "CoinName", "Class"`. You should maintain the index of the `crypto_df` DataFrames.

#### Visualizing Results

In this section, I creted some data visualization to present the final results. Perform the following tasks:

1. Create a scatter plot using `hvplot.scatter`, to present the clustered data about cryptocurrencies having `x="TotalCoinsMined"` and `y="TotalCoinSupply"` to contrast the number of available coins versus the total number of mined coins. Use the `hover_cols=["CoinName"]` parameter to include the cryptocurrency name on each data point.
(see Images folder)

2. Use `hvplot.table` to create a data table with all the current tradable cryptocurrencies. The table should have the following columns: `"CoinName", "Algorithm", "ProofType", "TotalCoinSupply", "TotalCoinsMined", "Class"`
