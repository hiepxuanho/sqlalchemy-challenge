# sqlalchemy-challenge

# Hawaii Climate Analysis

This project is designed to help plan a holiday trip to Hawaii, by providing climate insights through data analysis. We’ll use Python, SQLAlchemy, Pandas, and Matplotlib to perform a comprehensive analysis of precipitation and temperature trends for the area.

# Project Overview
This project performs a climate analysis and data exploration of Honolulu’s climate using an SQLite database. The analysis consists of:

1. Precipitation Analysis - Analyzing precipitation patterns over a specific period.
2. Station Analysis - Analyzing temperature trends and activity levels of different weather stations.

# Files Included
- climate_starter.ipynb: Jupyter notebook to execute and visualize the analysis.
- hawaii.sqlite: SQLite database containing climate data.


# Notes:

I got stuck at the part where to perform a query to retrieve the data and precipitation scores and find the date one year from the last date in data set. I was struggling to get the right answer, and went to search on Chat GPT to find the answer. Chat GPT used .strptime and .timedelta which I never knew before.

/--------------Chat GPT codes--------------------/

one_year_diff = dt.datetime.strptime(most_recent_date, "%Y-%m-%d") - dt.timedelta(days=365)

precipitation_data = session.query(Measurement.date, Measurement.prcp).\
    filter(Measurement.date >= one_year_diff).\
    order_by(Measurement.date).all()

/--------------Chat GPT codes--------------------/

While I was doing the summary statistic for the precipitation data.

// Calculate each summary statistic manually
precipitation_count = precipitation_df['precipitation'].count()
precipitation_mean = precipitation_df['precipitation'].mean()
precipitation_std = precipitation_df['precipitation'].std()
precipitation_min = precipitation_df['precipitation'].min()
precipitation_25 = precipitation_df['precipitation'].quantile(0.25)
precipitation_50 = precipitation_df['precipitation'].median()  # or use .quantile(0.5)
precipitation_75 = precipitation_df['precipitation'].quantile(0.75)
precipitation_max = precipitation_df['precipitation'].max()

I found out that we could use .describe() method in Pandas, which is much more simplier instead of calculating in the usual way.

/------------------------------------------/

precipitation_summary = precipitation_df['precipitation'].describe()

/-----------------------------------------/
