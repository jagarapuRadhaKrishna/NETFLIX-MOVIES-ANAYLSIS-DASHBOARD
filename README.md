# NETFLIX-MOVIES-ANAYLSIS-DASHBOARD
i am excited to Share My Latest Tableau Dashboard ! Hey everyone!  I’m thrilled to present my latest Tableau project, the Netflix Movies Analysis Dashboard, which was built using the kaggle dataset! This dashboard offers a comprehensive view of detail information of netflix movies and its collections , ratings  .

![Dashboard 1](https://github.com/user-attachments/assets/28cb917f-235a-4a6d-9b98-d83aa7dc188a)

# FEATURES OF THE DASHBOARD:

--> Interactive Visualizations: Explore different parameters through bar charts, line charts, and maps.

--> Comparisons: Easily compare the tv shows and movies of their ratings ,top 10 genres , total movies & tv shows by country & also by year  across multiple metrics with clean, visually appealing graphs.

--> Filtering Options: Users can filter by country/year & ratings to dive deeper into specific data sets.

--> Dynamic Insights: Use the dashboard to analysis to take the clarity on the netflix tv shows & movies on this netflix dashboard 

# DATA SET : 

[netflix_titles krishna.xlsx](https://github.com/user-attachments/files/17137635/netflix_titles.krishna.xlsx)

# TECHNOLOGIES USED:

--> Tableau (for data visualization)

--> Data pre-processing: Excel/CSV


# HOW TO ACCESS THE DASHBOARD:

1. Download or clone this repository.
2. Open the Tableau file (.twb or .twbx).
3. Explore the interactive dashboard.

   # CODE :

   import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px

# Sample data for the dashboard
data = {
    'Country': ['USA', 'India', 'UK', 'Brazil', 'Japan'],
    'Titles': [2032, 1567, 987, 743, 612],
    'Ratings': ['TV-MA', 'TV-14', 'TV-PG', 'R', 'PG'],
    'Genres': ['Documentaries', 'Stand-Up Comedy', 'Dramas, International Movies', 'Comedies, International Movies', 'Kids\' TV'],
    'Genres Count': [299, 273, 248, 174, 159],
    'Movies': [4265],
    'TV Shows': [1669],
    'Years': [1920, 1940, 1960, 1980, 2000, 2020],
    'Content Count': [100, 200, 400, 600, 1000, 1500]
}

# DataFrame for Total Movies & TV Shows by Country (Map)
df_map = pd.DataFrame({
    'Country': ['USA', 'India', 'UK', 'Brazil', 'Japan'],
    'Titles': [2032, 1567, 987, 743, 612]
})

# Plot: Total Movies & TV Shows by Country
fig_map = px.choropleth(df_map, 
                        locations="Country", 
                        locationmode="country names",
                        color="Titles", 
                        hover_name="Country", 
                        color_continuous_scale="reds", 
                        title="Total Movies & TV Shows by Country")
fig_map.show()

# Plot: Ratings Distribution
df_ratings = pd.DataFrame({
    'Ratings': ['TV-MA', 'TV-14', 'TV-PG', 'R', 'PG'],
    'Count': [2027, 1698, 701, 508, 286]
})
plt.figure(figsize=(10, 6))
sns.barplot(x='Ratings', y='Count', data=df_ratings, palette='Reds')
plt.title('Ratings Distribution')
plt.show()

# Plot: Movies vs TV Shows Distribution
plt.figure(figsize=(6,6))
labels = ['Movies', 'TV Shows']
sizes = [68.42, 31.58]
colors = ['#3498db', '#e74c3c']
plt.pie(sizes, labels=labels, colors=colors, autopct='%1.2f%%', startangle=140)
plt.axis('equal')
plt.title('Movies & TV Shows Distribution')
plt.show()

# Plot: Top 10 Genres
df_genres = pd.DataFrame({
    'Genres': ['Documentaries', 'Stand-Up Comedy', 'Dramas, International Movies', 
               'Comedies, International Movies', 'Kids\' TV'],
    'Count': [299, 273, 248, 174, 159]
})
plt.figure(figsize=(10, 6))
sns.barplot(x='Count', y='Genres', data=df_genres, palette='Reds')
plt.title('Top 10 Genres')
plt.show()

# Plot: Total Movies & TV Shows by Year
df_years = pd.DataFrame({
    'Year': [1920, 1940, 1960, 1980, 2000, 2020],
    'Count': [100, 200, 400, 600, 1000, 1500]
})
plt.figure(figsize=(10, 6))
plt.plot(df_years['Year'], df_years['Count'], color='blue', label='Movies')
plt.fill_between(df_years['Year'], df_years['Count'], color='blue', alpha=0.1)
plt.title('Total Movies & TV Shows by Year')
plt.xlabel('Year')
plt.ylabel('Number of Titles')
plt.show()

