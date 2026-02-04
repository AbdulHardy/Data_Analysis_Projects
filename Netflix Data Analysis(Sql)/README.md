# 🎬 Netflix Data Analysis (SQL + Power BI)

## 📌 Project Overview

This project analyzes Netflix’s movies and TV shows dataset to uncover insights about content distribution, audience targeting, regional contribution, and growth trends over time. The analysis was performed using **PostgreSQL** for data querying and **Power BI** for visualization.

The goal of this project is to demonstrate **end-to-end data analysis skills** — from data extraction and transformation using SQL to building an interactive and insight-driven dashboard in Power BI.

---

## 🛠️ Tools & Technologies

* **Database**: PostgreSQL
* **Visualization**: Power BI Desktop
* **Language**: SQL
* **Dataset Source**: Kaggle

---

## 📂 Dataset Information

* **Dataset Name**: Netflix Movies and TV Shows
* **Source**: Kaggle
* **Link**: [https://www.kaggle.com/datasets/shivamb/netflix-shows](https://www.kaggle.com/datasets/shivamb/netflix-shows)

### Dataset Contains:

* Movies and TV Shows available on Netflix
* Attributes include:

  * show_id
  * title
  * type (Movie / TV Show)
  * country
  * release_year
  * date_added
  * rating
  * duration
  * listed_in (genre)
  * director

---

## 🔄 Data Workflow

1. Downloaded dataset from Kaggle
2. Imported CSV into PostgreSQL
3. Cleaned and queried data using SQL
4. Connected PostgreSQL to Power BI
5. Built an interactive dashboard for analysis

---

## 📊 Dashboard Features & Analysis

### 🔹 Key Insights Covered:

* Total number of Netflix titles
* Movies vs TV Shows distribution
* Content distribution by rating
* Top countries producing Netflix content
* Top genres on Netflix
* Content growth trends over time
* Content growth before and after 2015
* Country-wise comparison of Movies vs TV Shows
* Recent content additions by country
* Genre popularity by content type

---

## 🧾 SQL Queries Used for Analysis

Below are the key SQL queries used in PostgreSQL to generate insights for the Power BI dashboard.

### 1️⃣ Total Number of Netflix Titles

```sql
SELECT COUNT(show_id) AS total_titles
FROM netflix_titles;
```

### 2️⃣ Movies vs TV Shows Distribution

```sql
SELECT type, COUNT(show_id) AS total
FROM netflix_titles
GROUP BY type;
```

### 3️⃣ Content Distribution by Rating

```sql
SELECT rating, COUNT(show_id) AS total
FROM netflix_titles
WHERE rating IS NOT NULL
GROUP BY rating
ORDER BY total DESC;
```

### 4️⃣ Top Countries by Number of Titles

```sql
SELECT country, COUNT(show_id) AS total
FROM netflix_titles
WHERE country IS NOT NULL
GROUP BY country
ORDER BY total DESC
LIMIT 10;
```

### 5️⃣ Top Genres on Netflix

```sql
SELECT listed_in, COUNT(show_id) AS total
FROM netflix_titles
GROUP BY listed_in
ORDER BY total DESC
LIMIT 10;
```

### 6️⃣ Content Release Trend by Year

```sql
SELECT release_year, COUNT(show_id) AS total
FROM netflix_titles
GROUP BY release_year
ORDER BY release_year;
```

### 7️⃣ Content Added Trend Over Time

```sql
SELECT EXTRACT(YEAR FROM date_added) AS year_added,
       COUNT(show_id) AS total
FROM netflix_titles
WHERE date_added IS NOT NULL
GROUP BY year_added
ORDER BY year_added;
```

### 8️⃣ Content Growth Before 2015

```sql
SELECT release_year, COUNT(show_id) AS total
FROM netflix_titles
WHERE release_year < 2015
GROUP BY release_year
ORDER BY release_year;
```

### 9️⃣ Content Growth After 2015

```sql
SELECT release_year, COUNT(show_id) AS total
FROM netflix_titles
WHERE release_year >= 2015
GROUP BY release_year
ORDER BY release_year;
```

### 🔟 Country vs Content Type

```sql
SELECT country, type, COUNT(show_id) AS total
FROM netflix_titles
WHERE country IS NOT NULL
GROUP BY country, type
ORDER BY total DESC;
```

### 1️⃣1️⃣ Top Directors by Content Count

```sql
SELECT director, COUNT(show_id) AS total
FROM netflix_titles
WHERE director IS NOT NULL
GROUP BY director
ORDER BY total DESC
LIMIT 10;
```

### 1️⃣2️⃣ Rating vs Content Type

```sql
SELECT rating, type, COUNT(show_id) AS total
FROM netflix_titles
WHERE rating IS NOT NULL
GROUP BY rating, type
ORDER BY total DESC;
```

### 1️⃣3️⃣ Top Countries by Recent Additions

```sql
SELECT country, COUNT(show_id) AS total
FROM netflix_titles
WHERE date_added >= CURRENT_DATE - INTERVAL '5 years'
  AND country IS NOT NULL
GROUP BY country
ORDER BY total DESC
LIMIT 10;
```

---

## 📈 Dashboard Preview
<img width="1920" height="1080" alt="Netflix_Data_Dashboard" src="https://github.com/user-attachments/assets/42521768-be1e-4d6d-a7b8-b54bf67bcc54" />

---

## 🧠 Business Insights

* Netflix content expanded rapidly after 2015
* The United States and India are the largest content contributors
* Movies dominate the platform compared to TV Shows
* TV-MA and TV-14 are the most common ratings, indicating a focus on mature audiences
* Drama and International content are among the most popular genres

---

## 🎯 What I Learned

* Writing SQL queries for real-world datasets
* Connecting PostgreSQL with Power BI
* Designing clean and informative dashboards
* Translating raw data into business insights
* Structuring data analysis projects for portfolios





⭐ If you found this project helpful, feel free to star the repository!
