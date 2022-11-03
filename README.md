## 👨‍💻Wayne Willis, Omondi
📞 ***+254768715840***, ***+254755976610***<br>
📧***wayneaudu6@outlook.com***<br>
📘[LinkedIn Profile](https://www.linkedin.com/in/waynewillislink/)<br>
📄<ins><a id="raw-url" href="https://raw.githubusercontent.com/WayneNyariroh/portfolio/main/Wayne_Willis_RESUME.pdf">My Resume</a></ins><br>

---
My journey into Data Science and Data Engineering.
> feel free to explore the source codes on the github repositories👍

### <ins>[1: Web Scraping: Criminal Minds TV Show Data](https://github.com/WayneNyariroh/criminalmindstv_webscraping_EDA)</ins>
Often the data we need for our projects, personal or professional, is not readily available. Web scraping is the process of extracting and parsing data from websites. It's a useful technique for gathering the data we need for sources online and creating our own datasets for analysis and vizualization.<br>
<br>
This project came up as I was watching the most recent season of one of my all-time favorite TV shows - Criminal Minds. I was curious about how the season rates and performances compared to the previous seasons; but the data was readily available on the IMDB Movies and Series Dataset on platforms like Kaggle. I had to 'extract' the data on Criminal Minds TV show from the relevant websites.<br>

> **Libraries used**: jupyter lab, python, pandas, bs4, lxml, requests <br>

Procedure:
- Used read_html() method where html data is in tables .i.e., the wikitables in Wikipedia.
- Used requests library to 'get' the IMBD web page(s) locally.
- Inspected HTML source on my browser to see the relevant tags that contained the information I needed.
- Used BeautifulSoup to parse (break into components) and extract relevant information. Considering the show had 15 seasons, for loop was necessary to extract information from each season. As show in the code snippet below.

```python
for season in range(15):
    season_number = season + 1
    imdb_url = f'https://www.imdb.com/title/tt0452046/episodes?season={season_number}' 
    imdb_response = get(imdb_url)
    season_html = BeautifulSoup(imdb_response.content)
    season_info = season_html.findAll('div', attrs={
        'class':'info'})
        
    for episode_number, episode in enumerate(season_info):
            episode_name = episode.strong.a.text       
            episode_description = episode.find(attrs={
                'class':'item_description'}).text.strip()
            episode_airdate = episode.find(attrs={
                'class':'airdate'}).text.strip()
            imdb_rating = episode.find(attrs={
                'class':'ipl-rating-star__rating'}).text
```
<ins>[View Scraping Code](https://github.com/WayneNyariroh/criminalmindstv_webscraping_EDA/blob/main/criminalminds-tv-data-scraping.ipynb)</ins><br>
- Created dataframes.
- Cleaned the data. The datasets' data types needed cleaning and convertion inorder for them to be in formats friendly to analysis and manipulation.
- Exported the scraped and cleaned data into relevant files.
- Did a quick Exploratory Data Analysis and Visualization. 

![Criminal minds Analysis!](/visualization_output/cmanalysiscopy.png)<br>

![Criminal minds Analysis!](/visualization_output/cmanalysiscopy2.png)<br>

<ins>[View Analysis Code and Outputs](https://github.com/WayneNyariroh/criminalmindstv_webscraping_EDA/blob/main/criminalminds-tv-data-analysis.ipynb)</ins><br>

---
### <ins>[2: Data Analysis & Visualization]</ins>
Every business is highly dependent on its data to make better decisions for growth and success, data analysis plays an important role in helping different business entities to get an idea on their performance and any opportunities to increase gains and minimise losses. <br>
The project is divided into three activities:<br>
a. Exploratory Data Analysis using Python<br>
b. Customer Retention Analysis using Python<br>
c. PowerBI Dashboard<br>

#### [(a) Exploratory Data Analysis](https://github.com/WayneNyariroh/StoreSales_Analysis/blob/main/superStoreSales_EDA.ipynb)

The objective was to gain valuable insights on the overall performance of the Store.
> **Tools used**: jupyter lab, python, pandas, numpy, matplotlib and seaborn. <br>
> **Activities**: data cleaning, data querying and vizualization. <br>
> **Concepts explored**: Correlation, Pivoting and Indexing, Date Manipulation. <br>

Insights:<br>
```python
no_of_sales_table = pd.pivot_table(store_df, values='Sales',
                    index='Order Year', columns='Order Month', aggfunc='count', margins=True)
 
plt.figure(figsize=(20,5))
plt.title('SuperStore - Number of Sales Each Month for the Review Period: 2015 - 2019', fontsize=11, fontweight='bold')
sns.heatmap(no_of_sales_table, cmap='Blues', annot=True, annot_kws={"size":11}, fmt="d", cbar=False) 
```

![Month and Sales!](/visualization_output/monthlysales.png)<br>

<ins> [View Code](https://github.com/WayneNyariroh/StoreSales_Analysis/blob/main/superStoreSales_EDA.ipynb)</ins>

#### [(b) Customer Retention: Performing a Cohort Analysis using Python](https://github.com/WayneNyariroh/customer-retention_cohortAnalysis/blob/main/RetentionAnalysis.ipynb)
Monitoring retention metrics is critical for a business to understand lifetime customer value and to quantify the efficacy of its marketing strategy and customer service program.
***Customer retention is when one of your buyers purchases from you again***.<br>

```python
retention_rates_2015 = cohort_table_2015.divide(cohort_table_2015.iloc[:,0], axis=0)

plt.figure(figsize=(20,8))
plt.title('SuperStore - Customer Retention Rates: 2015',fontsize=11, fontweight='bold')
sns.heatmap(retention_rates_2015, annot=True, cmap='Blues', fmt='.0%')
plt.show()
```

![Retention Rates!](visualization_output/cohortplots2.png)<br>

> *In the figure, Cohort Index 1 serves as the first month a customer made an order, hence the values is 100% for each cohort month. The values in the subsequent Cohort Index shows how many of the customers in that monthly cohort made a new order. i.e, in Cohort Index 2 a month after the first order, 4% of the customers who made an order in January 2015 made a new purchase with the store*<br>

A business' customer retention rate compares the number of customers you have retained to your total number of customers during a certain period. You can use customer loyalty programs, customer feedback surveys, social media and additional incentives to improve your customer retention rate.<br>
> **Tools used**: jupyter lab, python, pandas, matplotlib and seaborn. <br>
> **Activities**: Data processing, data cleaning, data querying, creating pivot tables, indexing, and vizualization. <br>
> **Concept explored:** Cohorts and retention.<br>


Clients are assigned to a cohort based on the first time they appeared in the dataset i.e, the time of first order, then their purchasing behaviour monitored over a duration. Concept of Cohorts and Retention Analysis can be extended to various organizations and institutions; a private clinic can use it to observe returning patients or monitor appointment keeping.<br>

<ins>[View Code](https://github.com/WayneNyariroh/customer-retention_cohortAnalysis/blob/main/RetentionAnalysis.ipynb)</ins>

#### [(c) PowerBI Visualization Project](https://github.com/WayneNyariroh/StoreSales_PowerBI_Dashboard)

![PowerBI Dashboard](/visualization_output/DashboardScreenshot.png)
> **Tools used**: Power BI

A simple and user-friendly dashboard that display annotations of each value and allows filtering on the visualizations and insights based on selected values, focusing on Revenue, Number of Sales and Profit to allow interactivity.<br>
 
<ins><a id="raw-url" href="https://raw.githubusercontent.com/WayneNyariroh/portfolio/main/Wayne_Willis_RESUME.pdf">Download Dashboard</a></ins><br>

---
