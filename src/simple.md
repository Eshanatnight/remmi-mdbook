# Simple Recommenders

Simple recommenders are basic systems that recommend the top items based on a certain metric or score. In this section, you will build a simplified clone of IMDB Top 250 Movies using metadata collected from IMDB.

    Note: The IMDB Dataset was removed due to a DMCA violation. We are now using the TMDb dataset.

## **Idea to Solve the Problem**

One of the most basic metrics one can think of is the ranking to decide which top 250 movies are based on their respective ratings.

However, using a rating as a metric has a few caveats:

* It does not take into consideration the popularity of a movie. Therefore, a movie with a rating of 9 from 10 voters will be considered 'better' than a movie with a rating of 8.9 from 10,000 voters.

* This metric will also tend to favor movies with a smaller number of voters with skewed and/or extremely high ratings. As the number of voters increases, the rating of a movie regularizes and approaches towards a value that is reflective of the movie's quality and gives the user a much better idea as to which movie they should choose. While it is difficult to discern the quality of a movie with extremely few voters, you might have to consider external sources to conclude.

Before getting started with this  -

* we need a metric to score or rate movie
* Calculate the score for every movie
* Sort the scores and recommend the best rated movie to the users.

We can use the average ratings of the movie as the score but using this won't be fair enough since a movie with 8.9 average rating and only 3 votes cannot be considered better than the movie with 7.8 as as average rating but 40 votes.
So, I'll be using IMDB's weighted rating (wr) which is given as :-

## **Weighted Average Rating**

We can use the Weightied Rating (WR) as a metric to rank our movies. The WR is a combination of the following:

![weighted-rating](.\images\weighted_rating.png)

where,

* v is the number of votes for the movie
* m is the minimum votes required to be listed in the chart
* R is the average rating of the movie
* C is the mean vote across the whole report

We will use cutoff m as the 90th percentile.
In other words, for a movie to be featured in the charts, it must have more votes than at least 90% of the movies on the list.
