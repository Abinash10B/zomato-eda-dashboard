# Zomato Restaurant Data — EDA & BI Dashboard

Exploratory analysis and an interactive Power BI dashboard built on Zomato
restaurant listings (Bengaluru), looking at how online ordering, table
booking, restaurant type, and cost relate to customer ratings and popularity.

## Files

- `Zomato_raw.csv` — original, unmodified source data (148 restaurants)
- `Zomato_cleaned.csv` — cleaned data (rate converted to numeric, columns
  renamed, rating/cost bands added — see cleaning steps below)
- `Zomato_EDA.ipynb` — full exploratory analysis notebook: cleaning, 13
  visualizations, and written insights after each chart

## Dataset

148 restaurants, 7 raw columns: `name`, `online_order`, `book_table`, `rate`,
`votes`, `approx_cost(for two people)`, `listed_in(type)`.

## Cleaning Steps (in `Zomato_EDA.ipynb`)

1. Converted `rate` from text (`4.1/5`) to a numeric value.
2. Renamed `approx_cost(for two people)` → `cost_for_two` and
   `listed_in(type)` → `restaurant_type`.
3. Checked for missing values — none found.
4. Checked for duplicate rows — none found.
5. Added `rating_band` and `cost_band` grouping columns for easier
   filtering/analysis.

## Key Findings

- **Dining** is the dominant category (110/148 restaurants) and accounts for the most total votes.
- Restaurants that accept **online orders** have a higher average rating (**3.86** vs **3.49**).
- Restaurants that accept **table bookings** have an even larger rating gap (**4.19** vs **3.60**).
- **Votes and rating** are moderately correlated (r = 0.49) — popularity tracks quality.
- **Cost** correlates weakly with both rating (r = 0.28) and votes (r = 0.32).
- Top restaurants by votes: **Empire Restaurant** (4,884 votes, 4.4★), **Meghana Foods**
  (4,401 votes, 4.4★), **Onesta** (2,556 votes, 4.6★).

## Power BI Dashboard

Built as a two-page interactive Power BI dashboard on top of the cleaned data:

**Page 1 — Overview:**
- 5 KPI cards: Avg Rating, Total Votes, Avg Cost for Two, % Online Order, Restaurant Count
- 3 comparison charts: avg rating by restaurant type, by online order availability, by table booking availability
- A scatter chart plotting votes vs. cost, colored by restaurant type and sized by rating
- 2 donut charts breaking down restaurants by rating band and cost band
- 4 slicers (restaurant type, online order, table booking, cost band) filtering the whole page

**Page 2 — Full Data:**
- A complete, sortable leaderboard of all 148 restaurants (name, type, rating, votes, cost, online order, table booking), sorted by votes descending

The dashboard is included as ZOMATO_project.pbix — open it directly in Power BI Desktop to explore it. It was built from Zomato_cleaned.csv following the analysis in the notebook.
## Tools

Python (pandas, matplotlib, seaborn), Jupyter Notebook, Power BI

## Next Steps

- Train a machine learning model to predict restaurant `rate` from the
  other features
