# Goodreads Recommender System

This repository contains the implementation of a robust recommender system for Goodreads, designed to enhance the user experience by providing personalized book recommendations. This system leverages a variety of machine-learning techniques, including content-based filtering, collaborative filtering, matrix factorization, neural collaborative filtering, and graph-based algorithms.


## Table of Contents

- [Introduction](#introduction)
- [Dataset](#dataset)
- [Methods](#methods)
  - [Content Filtering](#content-filtering)
  - [Collaborative Filtering](#collaborative-filtering)
  - [Neural Collaborative Filtering (NCF)](#neural-collaborative-filtering-ncf)
  - [Matrix Factorization Techniques](#matrix-factorization-techniques)
  - [Graph-Based Algorithms](#graph-based-algorithms)
- [Results](#results)
- [Conclusion](#conclusion)
- [Contributors](#contributors)
- [License](#license)

## Introduction

Goodreads is a renowned social cataloging website where users can explore books, write reviews, and manage their reading lists. Our recommender system aims to leverage the intrinsic and collaborative data from millions of user interactions to suggest books that align with individual preferences.

## Dataset

The Goodbooks-10k dataset encompasses six million ratings for ten thousand of the most popular books, detailed with extensive metadata. This dataset provides a robust foundation for building and evaluating recommender systems. Here is a breakdown of the contents:

- **ratings.csv**: Records user interactions with books, each entry consisting of a user ID, book ID, and a rating from 1 to 5, detailing how users have rated books over time.

- **to_read.csv**: Lists the books users intend to read, represented as pairs of user IDs and book IDs, which helps in analyzing user preferences for future readings.

- **books.csv**: Contains metadata for each book, including Goodreads IDs, authors, titles, average ratings, and publication years, offering a comprehensive view of the book attributes.

- **book_tags.csv**: Features tags or genres assigned to books by users, showing a book's Goodreads ID, a tag ID, and the count of times the tag was applied, arranged by popularity of tags.

- **tags.csv**: Maps numerical tag IDs to their descriptive names, clarifying the genres or thematic elements assigned to the books by the community.

For detailed file structures and smaller examples, see the files listed above in the repository.

Note that in the notebook, due to computational resource constraints and the need to maintain manageable inference time, we selected 10% of the users with more than 20 ratings.

## Methods

This project utilizes a variety of recommendation techniques to optimize the user experience on Goodreads by suggesting books tailored to their preferences. The methods are implemented as follows:

### Content Filtering
Content-based filtering employs descriptive features of books, such as titles, authors, and genres. These features are transformed into vector representations using methods like Word2Vec for textual data, and one-hot encoding for categorical data. This allows the system to compute similarities and recommend books similar to what a user has previously enjoyed.

### Collaborative Filtering
Collaborative filtering predicts user preferences based on the ratings and behaviors of similar users. It includes:
- **User-User Collaborative Filtering:** Identifies similar users based on ratings and recommends books based on what these similar users liked.
- **Item-Item Collaborative Filtering:** Recommends books by finding items similar to those the user has rated highly in the past.

### Neural Collaborative Filtering (NCF)
NCF enhances collaborative filtering by incorporating a neural network to capture the non-linear relationships between user and item interactions. This method uses a multi-layer perceptron to learn from the features representing users and items, providing a deep learning approach to recommendation.

### Matrix Factorization Techniques
Matrix factorization techniques decompose the user-item interaction matrix into lower-dimensional latent factors for users and items, and they include:
- **SGD-Based Matrix Factorization:** Utilizes Stochastic Gradient Descent to find the optimal latent factors by minimizing the prediction error.
- **ALS-Based Matrix Factorization:** Uses Alternating Least Squares to optimize the latent factors in a way that alternates between fixing user factors and solving for item factors, and vice versa, suitable for large-scale data.

### Graph-Based Algorithms
These methods use graph theory to improve recommendation quality, especially handling new users or items (cold-start problem) and large, sparse datasets:
- **GraphSage:** Generates embeddings by sampling and aggregating features from a node’s local neighborhood.
- **LightGCN:** Simplifies the graph convolution network by focusing on neighborhood aggregation without feature transformation and non-linear activation.
- **NGCF:** Integrates user-item interactions directly into the embedding process, enhancing the collaborative filtering by capturing high-order connectivities.

These methods are evaluated based on their ability to accurately predict user ratings and effectively rank recommendations, employing metrics such as RMSE, MAE, and NDCG across different training and testing configurations.


## Results

The performance of our recommender system was rigorously evaluated across various configurations to ensure robustness and accuracy. We used a comprehensive set of metrics to assess the effectiveness of the system in both rating predictions and ranking quality:

### Rating Prediction Metrics
- **Root Mean Square Error (RMSE):** Measures the average magnitude of the errors in predictions of ratings, with lower values indicating better performance.
- **Mean Absolute Error (MAE):** Calculates the average absolute difference between predicted and actual ratings, providing a straightforward measure of prediction accuracy.
- **R-squared (R²):** Indicates the proportion of variance in the dependent variable that is predictable from the independent variables, showing the strength of the relationship between predicted and actual ratings.

### Ranking Quality Metrics
- **Normalized Discounted Cumulative Gain (NDCG):** Evaluates the ranking quality of the recommendations by considering the position of relevant items, placing more importance on higher ranks.
- **Precision:** Measures the ratio of recommended items that are relevant, highlighting the accuracy of the recommendation.
- **Recall:** Assesses the ratio of relevant items that are recommended, reflecting the system's ability to capture all relevant items.
- **Mean Average Precision (MAP):** Provides an average precision score across all queries, offering insight into the overall precision of the system.

These metrics were applied across different train/test split configurations to mimic real-world scenarios and challenges, particularly focusing on few-shot learning where limited data is available. By analyzing the performance under these conditions, we were able to optimize our models to deliver accurate and reliable book recommendations.

## Conclusion

The evaluation reveals that different methods excel under different configurations. Techniques like SGD-SVD and ALS-SVD are robust in rating prediction tasks, whereas graph-based methods show promise in ranking tasks.

## Contributors

- **Arda Baris Basaran**
- **Louis Yann Nicolas Duval**

Electrical and Electronics Engineering Department, Neuro-X Department, EPFL, Lausanne, Switzerland

## License

This project is licensed under the MIT License - see the LICENSE.md file for details.
