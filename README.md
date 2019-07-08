# Movie Project

## Background

As part of a data science bootcamp, we (Denis Dunn and Anmol Srivats) did a project to try to make a 'successful' movie for a movie company. We were allowed to choose our own definition of 'success'. 

## Data Collection

### TMDB

We used TMDB's (The Movie Database) API, first to get a list of movies on TMDB, then to use that list to gather data for all movies on TMDB.  We found rouhly 20,000 movies on TMDB, and made it a point to gather data for all of them, because if we only looked at the most successful movies, our analysis would be biased, as it would appear that everything works out. The API limited us to 40 calls in 10 seconds, and we added a time delay to accomodate this, however, it would still occasionally block us out, and we had to make sure to try to get data for the same movie again, rather than moving on to the next one if it did so. 

### IMDB
The TMDB movie data also contained an IMDB url for the movie, so we built an IMDB scraper to gather IMDB data about those movies as well. Since it takes a long time to scrape 20,000 URLs, we split up the task into four parts, and ran each one individually, combining the data at the end. This is why our repository contains IMDB quart0-quart3. We added a random time delay to our scraper, to make sure it does not get blocked by IMDB. We also put every piece of data we try to gather into a 'try- except' loop, as IMDB page formats varied, and this could easily break our scraper. 

### SQL

We first merged the IMDB and TMDB data for movies, leaving around 17,000 movies that were populated for both. We then put this table into a SQL DB for future use, and also stored it as a .CSV as a back up. 

## Data Analysis

### Methodology
Our initial instinct was to look at 'profit' as success, defining profit as revenue- budget, however, we encountered two problems: 

1) Movie studios do not collect 100% of their revenue, some goes to theatres, distributors, etc. 

2) The average movie had 3.3x as much revenue as budget, making it seem like each movie was wildly successful

3) Some movies started to be made but were not completed, which is a hidden cost from our analysis

We decided to solve these problems by dividing each movie's revenue by 3.3, to make the average movie have 0 profit. i.e. Profit= Revenue/3.3 - Budget

### Findings

We found the correlation between each of our features and our new measures of profitability. Every single feature had an extremely weak correlation, except for IMDB rating, TMDB rating, and number of ratings. You would expect that movies with a high number of ratings had a large amount of revenue, as many people watched them, and then many people rated them. You find out both ratings, and number of ratings after the fact, and we found that the ratings themselves had a weak correlation with profitability (0.25). The profitability was also similar across genres, and across budgets.  

## Conclusions

We had many weak or negative conclusions in this project, and spend a lot of time invalidating various hypotheses of ours. While it was disappointing to not find a smoking gun, we also consider it a good thing in terms of experiment design that we did not figure out how to revolutionise the movie industry after a few hours of analysis. 




