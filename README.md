# 🎬 Movie Recommender System

A content-based movie recommendation system built on the **MovieLens Latest Small** dataset. Given a movie title, it finds and recommends 5 similar movies using cosine similarity on user rating patterns.

---

## 📌 How It Works

1. Loads `movies.csv` and `ratings.csv` from the MovieLens dataset
2. Merges them and builds a **user-movie pivot table** (rows = users, columns = movies, values = ratings)
3. Fills missing ratings with `0`
4. Computes **cosine similarity** between all movies based on user rating vectors
5. Given a movie, returns the top 5 most similar movies by similarity score
6. Includes a **fuzzy search** feature so you can find movies without knowing the exact title

---

## 🗂️ Project Structure

```
movie-recommender/
│
├── movie-recommender.ipynb     # Main notebook (Kaggle)
└── README.md
```

---

## 📊 Dataset

- **Source:** [MovieLens Latest Small](https://grouplens.org/datasets/movielens/latest/) via Kaggle
- **Files used:**
  - `movies.csv` — movie IDs, titles, genres
  - `ratings.csv` — user ratings (userId, movieId, rating, timestamp)

---

## ⚙️ Requirements

```
numpy
pandas
scikit-learn
```

All pre-installed in the Kaggle Python environment.

---

## 🚀 Usage

**Get recommendations for a movie (exact title):**

```python
recommend("Toy Story (1995)")
```

```
Recommended movies:
Babe (1995)
Lion King, The (1994)
Aladdin (1992)
GoodFellas (1990)
Silence of the Lambs, The (1991)
```

**Search by partial/fuzzy title:**

```python
find_movie("toy story")
# Returns: 'Toy Story'
```

---

## 🧠 Model Details

| Component | Detail |
|---|---|
| Approach | Collaborative filtering (user-based) |
| Similarity metric | Cosine similarity |
| Matrix | User × Movie pivot table |
| Missing values | Filled with `0` |
| Recommendations | Top 5 most similar movies |
| Fuzzy search | `difflib.get_close_matches` on cleaned titles |

---

## 📝 Notes

- Movie titles in the dataset include the release year e.g. `Toy Story (1995)`. The `find_movie()` function strips the year so you can search naturally.
- The model is user-rating based — movies are similar if users tend to rate them similarly, not necessarily because of shared genres.
- Built and tested on **Kaggle** using the Kaggle Python Docker environment.

---

## 📄 License

This project uses the [MovieLens dataset](https://grouplens.org/datasets/movielens/) provided by GroupLens Research for non-commercial use.
