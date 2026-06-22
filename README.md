Project Overview :- 

This project is a Ecommerce Product Recommendation System for an e-commerce website. Its main goals are to make shopping more personal for users, help them discover items they will like, and increase sales for the business.

It analyzes how users interact with products (like their rating history) and uses Machine Learning to predict what else they might want to buy.

The Dataset
What it contains: The project uses an Amazon dataset containing user ratings for electronic products.

Anonymization: To keep things fair and unbiased, the dataset doesn't use real names. Every user and every product is given a unique secret ID number.

The Three Recommendation Methods
Your system uses three different approaches to recommend the top 5 products depending on the situation:

1. Rank-Based Product Recommendation (For New Users)
Goal: Recommend the most popular items. This is perfect for new customers where the system doesn't know anything about their personal taste yet.

How it works: 1. The system calculates the average rating for every single product.
2. It counts the total number of ratings (interactions) each product received.
3. It sorts the products by their average rating, but only includes items that have met a minimum popularity threshold (e.g., at least 50 or 100 ratings). This prevents a product with just one 5-star rating from looking better than a product with thousands of 4.8-star ratings.

2. Similarity-Based Collaborative Filtering (For Logged-in Users)
Goal: Give personalized recommendations by finding "shopping buddies"—other users who share similar tastes.

How it works:

User ID Setup: The system converts text-based user IDs into simple numbers (from 0 to 1539) to make math calculations easier.

Finding Similar Users: The system uses a mathematical tool called Cosine Similarity to compare the target user's ratings against everyone else. It creates a ranked list of users who rate items most similarly to our target user.

Making the Recommendation: The system looks at what these "similar users" liked. It finds top-rated products that the similar users bought, but our target user hasn't seen yet, and recommends those.

3. Model-Based Collaborative Filtering (Advanced Personalization)
Goal: Provide highly accurate personal recommendations while solving two major real-world problems: Sparsity (most users only rate a tiny fraction of the thousands of products available) and Scalability (handling millions of users/products efficiently).

How it works:

Compressing the Data: The system takes the giant grid of user ratings and turns it into a "CSR Matrix." This is a programming trick that ignores all the empty blank spaces (where users haven't rated items) to save computer memory and speed up calculations.

Singular Value Decomposition (SVD): SVD is a smart math shortcut. It shrinks the giant dataset down into 50 "hidden themes" or "latent features" (like a product being "techy," "budget-friendly," or "durable") instead of looking at thousands of individual data points.

Predicting the Blanks: By multiplying these shrunk-down math matrices back together, the system calculates a predicted rating for every single product the user hasn't even looked at yet.

The Recommendation: It filters out items the user already bought, sorts the remaining products by their highest predicted ratings, and shows the top 5.

How the Model is Evaluated:
To make sure these predictions are actually good, the system calculates the RMSE (Root Mean Squared Error):

It compares the average actual ratings given by users against the average predicted ratings calculated by the SVD model.

By finding the mathematical difference between the two, it tells us how "wrong" or "right" the system's guesses are. A lower RMSE score means the system is highly accurate at guessing what users will like.
