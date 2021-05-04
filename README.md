# Machine Learning Projects


This is a continuously updating repository of several projects applying machine learning skills to solve real life problems of interesting topics.

## [01. Music Genre Classification]()

* **Target**: Classify genres of music tracks with music features extracted from librosa
* **Data Description**: 
    - Size: 1.3GB, 12MB
    - Data Type: wav, csv
    - Data Source: [GTZAN Dataset](https://www.kaggle.com/andradaolteanu/gtzan-dataset-music-genre-classification)
* **Tools**: Python, sklearn, librosa
* **Algorithms**: Random Forest, PCA
* **Data Pipeline**:
    - Feature Extraction: A [demo]() of how to extract features from .wav files was implemented, while the extraction of all tracks was not processed as kaggle provided the dataset with music features being extracted already.
    - Feature Engineering: 
        * StandardScaler and QuantileTransformaer was applied to standardize and normalize the features as required by PCA or linear models
        * TargetEncoder was applied to encode the target variable
        * PCA was applied to simplify the model by reducing 57 features to 13 components
    - Model Selection and Hyperparameter Tuning:
        * A randomized search with corss validaiton was applied among LogisticsRegression, RidgeClassifier, and RandomForest to find the best model
        * A randomized search with cross validation was applied to find the best hyperparameters of RandomForest to improve the performance
    - Evaluation: A corss validation with "accuracy" as scoring metrics was applied to evaluate the performance of the model.


## [02. Artist Clustering with Music Track Tags]()

* **Target**: Clustering artists for recommendation with tags of their music tracks
* **Data Description**: 
    - Size: 5.3GB
    - Data Type: json
    - Data Source: [Million Songs](http://millionsongdataset.com/)
* **Tools**: PySpark, AWS S3, AWS EMR
* **Algorithms**: KMeans, TFIDF
* **Data Pipeline**:
    All the data transactions were processed on AWS.
    - Preprocessing: The most common tags were extracted from each track as the tags of an artist, and then transformed into TFIDF vectors for each artist;
    - Hyperparameter Tuning: The best k was found to optimize the euclidean distance score for Kmeans model.
    - Clustering Component Analysis: An "assumed label" was created, and the gini impurity of this "fake" label was calculated in each cluster to interpret the clustering result.
