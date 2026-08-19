
# Mumbai Affordable Restaurant Recommendation and Analytics System

## Project Overview

This project develops a content-based recommendation system for affordable and well-rated restaurants in specific areas of Mumbai (Andheri, Vile Parle, Juhu, Versova, Santacruz, Bandra). Utilizing a Zomato dataset, the system aims to help users discover dining options that align with their preferences for cuisine, price, and quality. Beyond recommendations, the project provides data analysis for deeper insights and prepares data for interactive visualization in Tableau.

## Features

*   **Robust Data Loading**: Handles various CSV delimiters and common parsing errors.
*   **Data Cleaning & Preprocessing**: Standardizes column names, removes duplicates, cleans text data, and converts data types.
*   **Targeted Area Filtering**: Focuses on specific Mumbai regions, including intelligent exclusion of 'Bandra Kurla Complex' from 'Bandra'.
*   **Advanced Feature Engineering**: Creates new features like `PRICE_CATEGORY`, `RATING_CATEGORY`, `POPULARITY_CATEGORY`, `AFFORDABLE_FLAG`, `WEIGHTED_RATING` (IMDB-like formula), and `VALUE_SCORE`.
*   **Content-Based Recommendation Model**: Implements a TF-IDF vectorizer on combined restaurant features to calculate similarity and recommend restaurants based on user preferences, incorporating weighted ratings and value scores.
*   **Exploratory Data Analysis (EDA)**: Visualizes key distributions and relationships of engineered features.
*   **Model Persistence**: Saves the trained TF-IDF vectorizer and crucial model metadata.
*   **Tableau Data Export**: Prepares and exports cleaned and processed data into CSV format, along with summary files, suitable for interactive dashboards.
*   **Project Documentation**: Generates `requirements.txt`, `.gitignore`, `dataset_source.md`, and a comprehensive `README.md`.

## Project Structure

```
mumbai-restaurant-recommender/
├── data/                        # Raw and processed datasets
├── models/                      # Saved recommendation model components (TF-IDF vectorizer, metadata)
├── notebooks/                   # Jupyter notebooks (e.g., this Colab notebook converted)
├── output/                      # General output files (e.g., intermediate data)
├── tableau/                     # CSVs exported for Tableau dashboards & Tableau guide
├── images/                      # Plots and visualizations generated during EDA
├── .gitignore                   # Files and directories to be ignored by Git
├── requirements.txt             # Python package dependencies
├── dataset_source.md            # Information about the dataset used
└── README.md                    # Project overview and instructions
```

## Getting Started

### Prerequisites

*   Python 3.8+
*   Jupyter Notebook or Google Colab environment
*   Required Python packages (see `requirements.txt`)

### Installation

1.  **Clone the repository (if applicable)**:
    ```bash
    git clone <repository_url>
    cd mumbai-restaurant-recommender
    ```

2.  **Install dependencies**:
    ```bash
    pip install -r requirements.txt
    ```

### Usage

1.  **Data Upload**: Ensure your `Zomato_Mumbai_Dataset.csv` (or similar Zomato-like dataset) is uploaded to the Colab environment or placed in the `data/` directory.
2.  **Run the Notebook**: Execute the cells sequentially in the provided Jupyter/Colab notebook (`mumbai_restaurant_recommender.ipynb`). The notebook will guide you through:
    *   Data loading and cleaning
    *   Feature engineering
    *   Exploratory Data Analysis
    *   Building and testing the recommendation model
    *   Saving model artifacts and exporting data for Tableau
3.  **Generate Recommendations**: Use the `recommend_restaurants` function with your preferences:
    ```python
    recommendations = recommend_restaurants(
        user_preferences="North Indian, casual dining",
        area="Andheri",
        price_category="Budget",
        rating_category="Good",
        top_n=10
    )
    print(recommendations)
    ```
4.  **Tableau Integration**: The exported CSV files in the `tableau/` directory can be imported into Tableau to create interactive dashboards. Refer to `tableau_dashboard_guide.md` for visualization ideas.

## Methodology

### Data Sources

The primary dataset is a CSV file containing Zomato restaurant data for Mumbai.

### Data Processing

*   **Cleaning**: Handled missing values, duplicates, and inconsistent data formats. Converted relevant columns to numeric types.
*   **Standardization**: Standardized region names and restaurant types to ensure consistent categorization.
*   **Feature Engineering**: Derived categorical features (Price, Rating, Popularity categories) and continuous scores (`WEIGHTED_RATING`, `VALUE_SCORE`) to capture restaurant attributes comprehensively.

### Recommendation Model

The core recommendation logic is based on a **Content-Based Filtering** approach:

1.  **Combined Features**: Restaurant features (Name, Cuisines, Restaurant Type, Price Category, Rating Category, Popularity Category) are concatenated into a single text string.
2.  **TF-IDF Vectorization**: A `TfidfVectorizer` converts these combined text features into numerical vectors, emphasizing words unique to specific restaurant profiles.
3.  **User Preference Vector**: User input preferences are similarly vectorized.
4.  **Cosine Similarity**: Cosine similarity is calculated between the user preference vector and all restaurant vectors to find the most similar restaurants.
5.  **Hybrid Scoring**: The TF-IDF similarity score is combined with `WEIGHTED_RATING` and `VALUE_SCORE` to produce a robust `COMBINED_SCORE`, ensuring recommendations are not only similar in content but also high in quality and value.

## Dependencies

All Python dependencies are listed in `requirements.txt`.

## License

This project is open-sourced under the MIT License. See the LICENSE file for more details. (Note: A separate LICENSE file would need to be created if not already present.)

## Contact

For any questions or suggestions, please open an issue in the GitHub repository.
