
# Tableau Dashboard Guide for Mumbai Restaurant Recommender

This guide outlines key visualizations and insights you can create in Tableau using the exported data from the Mumbai Restaurant Recommendation System. The following CSV files are available in the `tableau/` directory:

1.  `restaurants_model_data.csv`: Main dataset with all engineered features.
2.  `area_summary.csv`: Count of restaurants per area.
3.  `cuisine_summary.csv`: Count of restaurants per cuisine.

---

## Data Sources in Tableau:

*   **Data Source 1**: `restaurants_model_data.csv`
*   **Data Source 2**: `area_summary.csv`
*   **Data Source 3**: `cuisine_summary.csv`

---

## Suggested Visualizations:

### 1. Restaurant Overview Map

*   **Data Source**: `restaurants_model_data.csv`
*   **Type**: Map
*   **Columns to Use**:
    *   `REGION` or `AREA` (for location)
    *   `NAME` (Detail)
    *   `RATING` (Color/Size)
    *   `PRICE` (Tooltip)
    *   `CUISINE_CATEGORY` (Tooltip/Filter)
    *   `WEIGHTED_RATING`, `VALUE_SCORE` (Tooltip)
*   **Insight**: Visualize geographical distribution of restaurants, identify highly-rated areas, and examine price variations.

### 2. Price Category vs. Rating/Value Score

*   **Data Source**: `restaurants_model_data.csv`
*   **Type**: Bar Chart or Box Plot
*   **Columns to Use**:
    *   `PRICE_CATEGORY` (Columns)
    *   `WEIGHTED_RATING` (Rows)
    *   `VALUE_SCORE` (Rows - create a separate chart or use dual axis)
*   **Insight**: Understand how price level correlates with perceived quality and value.

### 3. Top Cuisines by Popularity

*   **Data Source**: `cuisine_summary.csv`
*   **Type**: Bar Chart
*   **Columns to Use**:
    *   `CUISINE` (Rows)
    *   `COUNT` (Columns)
*   **Insight**: Identify the most prevalent cuisine types in Mumbai's target areas.

### 4. Area-wise Restaurant Counts

*   **Data Source**: `area_summary.csv`
*   **Type**: Bar Chart
*   **Columns to Use**:
    *   `AREA` (Rows)
    *   `COUNT` (Columns)
*   **Insight**: Show the distribution of restaurants across the selected Mumbai areas.

### 5. Recommendation Filter Interface

*   **Data Source**: `restaurants_model_data.csv`
*   **Type**: Filters, Parameters, and possibly a list of recommended restaurants
*   **Columns to Use**: `AREA`, `PRICE_CATEGORY`, `RATING_CATEGORY`, `POPULARITY_CATEGORY`
*   **Insight**: Create interactive filters mirroring the recommendation function's inputs to dynamically filter the map or list of restaurants.

---

## Dashboard Design Tips:

*   **Interactivity**: Use filters and parameters to allow users to explore the data dynamically.
*   **Tooltips**: Customize tooltips to display relevant restaurant details on hover.
*   **Color Coding**: Use color to highlight important metrics (e.g., higher ratings in green).
*   **Layout**: Arrange visualizations logically for easy interpretation.
*   **Actions**: Implement filter actions between charts (e.g., clicking on an area in one chart filters other charts).

This guide provides a starting point. Feel free to explore other visualizations and combine these ideas to create a comprehensive and insightful dashboard!
