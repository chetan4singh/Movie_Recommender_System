# Movie_Recommender_System

A content-based movie recommendation system that suggests similar movies based on plot, genre, cast, and crew. Built using the TMDB 5000 Movies dataset, it transforms movie metadata into feature vectors and uses cosine similarity to find and recommend the top 5 most similar movies for any given title.

📌 Overview

This project answers a simple question: "If I liked this movie, what should I watch next?"

Instead of relying on user ratings or watch history (collaborative filtering), this system analyzes the content of each movie — its overview, genres, keywords, cast, and director — to find movies that are similar in nature.

🗂️ Dataset
TMDB 5000 Movie Dataset (from Kaggle)
tmdb_5000_movies.csv — movie metadata (overview, genres, keywords, etc.)
tmdb_5000_credits.csv — cast and crew information
⚙️ How It Works
Data Merging – Combines the movies and credits datasets on the title column.
Feature Selection – Keeps only relevant columns: movie_id, title, overview, genres, keywords, cast, crew.
Data Cleaning & Parsing – Converts stringified JSON columns (genres, keywords, cast, crew) into clean Python lists.
Feature Engineering – Extracts the top 3 cast members and the director, removes spaces from names (e.g., SamWorthington) to avoid duplicate token collisions, and combines everything into a single tags column.
Vectorization – Uses CountVectorizer (Bag-of-Words, top 5000 features, English stopwords removed) to convert the tags text into numerical vectors.
Similarity Computation – Calculates pairwise cosine similarity between all movie vectors.
Recommendation – For a given movie title, retrieves the top 5 most similar movies based on similarity score.
🛠️ Tech Stack
Python
Pandas & NumPy – data manipulation
Scikit-learn – CountVectorizer, cosine_similarity
Jupyter Notebook / Kaggle Notebook
🚀 Getting Started
Prerequisites
bash
pip install pandas numpy scikit-learn
Dataset

Download the dataset from Kaggle: TMDB 5000 Movie Dataset and place tmdb_5000_movies.csv and tmdb_5000_credits.csv in the project directory.

Run

Open and run Movie_Recommender_System.ipynb in Jupyter Notebook or Kaggle.

Example Usage
python
recommend('Batman Begins')

Output:

The Dark Knight
The Dark Knight Rises
Batman Begins
Batman
Batman Returns
📈 Future Improvements
Add a Streamlit web app for an interactive UI with movie posters
Incorporate TF-IDF or word embeddings for improved similarity scoring
Add collaborative filtering for a hybrid recommendation approach
