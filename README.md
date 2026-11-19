# Netflix Content Insights Dashboard | Power BI

An interactive Power BI dashboard that analyzes Netflix's catalog of movies and TV shows: what content exists, where it comes from, and how the catalog has grown over time.

![Netflix Content Insights Dashboard](dashboard.png)
## Business Questions Answered
- How big is the catalog, and what's the Movie vs TV Show split?
- Which countries and genres dominate the catalog?
- How has the number of titles added per year changed?
- Which age ratings are most common?
- How is content distributed by release decade?

## Key Insights
- The catalog has **8,807 titles**: **6,131 movies (69.6%)** and **2,676 TV shows (30.4%)**.
- The average movie runs about **99.6 minutes**.
- The **United States** leads with 3,689 titles, followed by **India** (1,046) and the **United Kingdom** (806).
- **Dramas** and **Comedies** are the most common genres.
- **TV-MA** is the most common rating (3,207 titles), pointing to a strong focus on mature audiences.
- Titles added per year grew quickly from 2016 and peaked around **2019**.
- The 2020s bar covers only 2020 to 2021, so it is a partial decade.

## Tools Used
- **Power BI Desktop** for visualization and dashboard design
- **Power Query** for data cleaning and transformation
- **DAX** for measures

## Data Cleaning (Power Query)
- Trimmed and cleaned text columns
- Found 2 corrupted rows where line breaks split records, and removed them (8,809 to 8,807 titles)
- Split multi-value genre and country columns into separate tables (`Netflix_Genres`, `Netflix_Countries`)
- Created `added_year`, `release_decade` and `duration_value` columns
- Handled null and error values

## DAX Measures
```DAX
Total Titles = DISTINCTCOUNT(Netflix_Titles[show_id])
Total Movies = CALCULATE([Total Titles], Netflix_Titles[type] = "Movie")
Total TV Shows = CALCULATE([Total Titles], Netflix_Titles[type] = "TV Show")
Avg Movie Duration = CALCULATE(AVERAGE(Netflix_Titles[duration_value]), Netflix_Titles[type] = "Movie")
```

## Dashboard Features
- Slicers for Type, Rating, Country and Genre
- KPI cards, donut chart, line chart, bar charts and column charts
- Dark Netflix-style theme with a consistent layout

## How to Use
1. Download `Netflix_Content_Insights.pbix`.
2. Open it in [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free, Windows only).
3. Use the slicers to explore the data.

## Data Source
Netflix Movies and TV Shows dataset from [Kaggle](https://www.kaggle.com/) (add the exact dataset link here).

## Author
**[Your Name]** | [LinkedIn profile link]
