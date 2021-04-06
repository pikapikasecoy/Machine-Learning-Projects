# Machine-Learning-with-Million-Song-Dataset

Data Source: http://millionsongdataset.com/

## Project Description
This is a repository with several projects related to Million Song Dataset. So far, only the first project has been done. This repo will be kept updating with more exploratory to this dataset.

### 1. Artist Clustering with Music Track Tags


#### 1.1 Data Description and Pipeline

This project mainly focused on "Last.fm" dataset, in this dataset, each track has a json file with information about "track id", "artist", "tags", "similar track id" with their "similarity score". You can also reach the detailed description here.
http://millionsongdataset.com/lastfm/

We uploaded all these datasets to a S3 bucket, and then do all the preprocessing and machine learning stuff on EMR with a PySpark Kernnel.

#### 1.2 Preprocessing
a) We extracted the first 10 similar tracks with the highest similarity scores
b) We extracted the top tag with the highest tag count for each track
c) We combined all these json files into one pyspark dataframe, and wrote them back to the S3 bucket as parquet files

#### 1.3 Artist Clustering
First, we extracted all the most common tags of each track for artists, and then transform these tags arrays into TFIDF vectors.

Then we applied a KMeans model to cluster artists with these sparse vectors, and found a best k with a local maximum squared Euclidean distance.

To interpret the clustering result, we also created a “fake label” with the most common tag of each artist, and calculate the gini impurity of this “fake label” in each cluster, then the weighted one for all clusters with the number of artists in each cluster.
