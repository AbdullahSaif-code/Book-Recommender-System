# Book Recommender System

A machine learning-based web application that recommends books to users based on collaborative filtering and popularity metrics. The project uses Flask for the web interface and processes the Book-Crossing dataset for recommendations.

---

## Table of Contents

- [Features](#features)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Data Sources](#data-sources)
- [How it Works](#how-it-works)
- [Screenshots](#screenshots)
- [Contributing](#contributing)
- [License](#license)

---

## Features

- **Top 50 Books:** Displays the most popular books based on ratings and votes.
- **Personalized Recommendations:** Suggests similar books based on user input.
- **Autocomplete:** Book search with autocomplete suggestions.
- **Responsive UI:** Clean, modern interface using Bootstrap.
- **Pre-trained Models:** Fast recommendations using precomputed similarity and popularity data.

---

## Project Structure

```
.gitignore
app.py
requirements.txt
Models/
    books.pkl
    piviot_table.pkl
    popular.pkl
    similarity_scores.pkl
Preprocissing/
    Books.csv
    Preprocing.ipynb
    Ratings.csv
    Users.csv
static/
    autocomplete.js
    styles.css
templates/
    index.html
    recommend.html
```

- **app.py**: Main Flask application.
- **Models/**: Serialized (pickle) files for fast loading of book data, pivot tables, popular books, and similarity scores.
- **Preprocissing/**: Raw datasets and Jupyter notebook for data cleaning and feature engineering.
- **static/**: CSS and JavaScript assets.
- **templates/**: HTML templates for the web interface.

---

## Installation

1. **Clone the repository:**
   ```sh
   git clone <repo-url>
   cd Book-Recommender-System
   ```

2. **Create a virtual environment (recommended):**
   ```sh
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```sh
   pip install -r requirements.txt
   ```

4. **Run the application:**
   ```sh
   python app.py
   ```
   The app will be available at [http://127.0.0.1:5000](http://127.0.0.1:5000).

---

## Usage

- **Home Page:** Shows the top 50 most popular books with their cover, title, author, votes, and average rating.
- **Recommend Page:** Enter a book name to get similar book recommendations. Autocomplete helps you find the correct title.

---

## Data Sources

- **Books.csv:** Book metadata (ISBN, title, author, publisher, year, image URLs).
- **Ratings.csv:** User ratings for books.
- **Users.csv:** User demographic data.

All datasets are from the [Book-Crossing Dataset](http://www2.informatik.uni-freiburg.de/~cziegler/BX/).

---

## How it Works

1. **Data Preprocessing:**  
   - Clean and merge datasets in [`Preprocissing/Preprocing.ipynb`](Preprocissing/Preprocing.ipynb).
   - Filter books with a minimum number of ratings for popularity.
   - Create a pivot table of users vs. books for collaborative filtering.

2. **Model Building:**  
   - Compute similarity scores between books using cosine similarity.
   - Store precomputed data in `.pkl` files for fast loading.

3. **Web Application:**  
   - Flask serves the UI and handles user requests.
   - On the home page, loads and displays the top 50 books from [`Models/popular.pkl`](Models/popular.pkl).
   - On the recommend page, takes user input, finds the closest matching book, and returns similar books using [`Models/similarity_scores.pkl`](Models/similarity_scores.pkl).

---

## Screenshots

> _Add screenshots of the home page and recommendation page here for better illustration._

---

## Contributing

1. Fork the repository.
2. Create your feature branch (`git checkout -b feature/YourFeature`).
3. Commit your changes (`git commit -am 'Add some feature'`).
4. Push to the branch (`git push origin feature/YourFeature`).
5. Open a pull request.

---

## License

This project is licensed under the MIT License.

---

## Acknowledgements

- [Book-Crossing Dataset](http://www2.informatik.uni-freiburg.de/~cziegler/BX/)
- Flask, Pandas, Scikit-learn, Bootstrap
