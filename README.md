# 🎬 IMDb & TMDB Movies Data Analysis

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

## 📊 Exploratory Data Analysis (EDA)
The analysis uncovered several key insights visualized using Seaborn:

* **Production Hubs:**    * Identified the top 5 countries producing the most content.
* **Financial Analysis:** 

[Image of Revenue Chart]

    * Analyzed revenue trends over the years to spot the "Golden Era" of cinema.
    * Highlighted production companies with the lowest revenue performance.
* **Ratings Distribution:** 
    * Examined the distribution of viewer votes to understand audience bias.

## 🚀 How to Run
1.  Clone the repository.
2.  Install dependencies:
    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn
    ```
3.  Run the analysis script:
    ```bash
    python movie_analysis.py
    ```

