# 🎬 IMDb & TMDB Movies Data Analysis
<img width="732" height="643" alt="image" src="https://github.com/user-attachments/assets/beea9e1e-cf76-492c-b746-d21124b6674a" />
<img width="544" height="475" alt="image" src="https://github.com/user-attachments/assets/7109784c-2998-4a24-992b-a5ea62ba23ed" />

## 📌 Project Overview
This project is an end-to-end data analysis pipeline built with **Python**. It involves cleaning, processing, and analyzing a massive dataset of movies (metadata, credits, keywords, and ratings). 
The goal was to transform raw, messy data into structured insights, handling complex data types like JSON strings and performing advanced missing value imputation using Machine Learning techniques.

## 🛠️ Technologies & Libraries Used
* **Python**: Core programming language.
* **Pandas**: For data manipulation, merging, and complex transformations.
* **NumPy**: For numerical operations.
* **Scikit-Learn (IterativeImputer)**: For advanced missing value imputation.
* **AST (Abstract Syntax Trees)**: To parse stringified JSON columns.
* **Matplotlib & Seaborn**: For static data visualization.

## ⚙️ Key Data Processing Steps

### 1. Data Cleaning & Parsing (The Tricky Part)
The raw dataset contained nested JSON objects within columns like `cast`, `crew`, and `keywords`.
* Used `ast.literal_eval` to safely evaluate string columns into Python objects.
* **Exploded** nested lists and flattened dictionaries to extract specific attributes (e.g., Actor Name, Director, Keywords).
* Separated `Cast` and `Crew` into distinct analytical tables linked by `movie_id`.

### 2. Advanced Missing Value Imputation 🧠
Instead of simply filling missing **Budget** and **Revenue** values with the mean (which can be misleading), I used **Multivariate Imputation by Chained Equations (MICE)** via `sklearn.impute.IterativeImputer`.
* The model predicted missing financial data based on correlations with other features like `vote_count`, `popularity`, and `runtime`.
* This ensured the data remained statistically valid for analysis.

### 3. Feature Engineering
* Converted timestamps to datetime objects.
* Extracted `Release Year` for temporal analysis.
* Standardized `IMDb ID` formats for potential merging with other datasets.



