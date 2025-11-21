Spotify Song Popularity Analysis — Big Data & Regression Modeling

This project explores the relationship between various audio features and song popularity using large-scale data processing and distributed computing tools. The goal was to clean, transform, and analyze a massive Spotify dataset, then build and evaluate a regression model capable of predicting a song’s popularity score from its numerical attributes.

Dataset (Must Be Downloaded Separately)

This project uses the “500K+ Spotify Songs with Lyrics, Emotions & More” dataset.
Due to its size (~500k rows, 39 columns, ~1GB), the dataset is NOT included in this repository.

You must download it manually:

Source: Kaggle

Dataset name: 900k Spotify Dataset (includes the 500k subset used here)

After downloading, place the dataset into your data directory (e.g. data/spotify.csv) or adjust paths in the notebook/code.

🛠️ Tools & Technologies

Apache Spark / PySpark — distributed processing, cleaning, transformation

Amazon Athena — SQL querying and schema management over S3

AWS S3 — storage for large dataset

Python — analysis and modeling

Spark MLlib (Regression) — building and evaluating predictive model

Project Workflow
1. Data Cleaning & Preprocessing (Spark)

Removed non-numerical and irrelevant fields

Converted categorical columns (e.g., explicit) to Boolean

Dropped nulls and duplicates

Standardized types (int/float) across all numerical fields

Addressed skewed distributions in continuous variables

Checked for multicollinearity and removed redundant features

2. Distributed Querying (Athena)

Created external Athena tables pointing to the dataset in S3

Queried large segments of the dataset without loading all data locally

Managed schema inconsistencies caused by multi-genre and multi-lyric fields

3. Regression Model Development

Built a regression model to predict popularity (0–100 scale)

Evaluated performance using RMSE and R² metrics

Analyzed feature importance to understand key predictors

4. Results

Achieved an RMSE of ~14

Found that Boolean features like “good for driving” and “good for party” had the strongest impact

Determined that many audio metrics alone cannot capture the full complexity of song popularity

Challenges

Managing large-scale data without overloading memory (especially when using Pandas)

Working with Athena’s schema rigidity when columns changed

Handling multi-label genre fields and comma-separated lyrics

Addressing skewed and imbalanced features

Future Improvements

Enhance features by encoding genres and lyrics properly

Explore alternative modeling techniques beyond basic regression

Integrate external data (artist popularity, release trends, social media influence)

Expand analysis by genre-specific pipelines
