## Do Oscar-winning films generally have higher ratings compared to non-winning nominees and top box-office hits?  (Q1)



So, do you think that if your favorite movie gets an oscar, it will get to the top ratings ? 
Well, let's find out !
But before going deep into the analysis, let's start simple, let's see how the ratings are distributed between oscar winners and nominees.

<div>
  {% include question1/boxplot.html %}
</div>

Interesting, we see that the winners seems to have a higher ratings. 

<!-- Oscaro : Nice ! So we are done, winning me will get you to the top ! -->

Well well, not that fast. While those results are encouraging, we still need to see if they are significant !
To do so, we'll use a simple t-test and see if the distribution are different. What's a t-test you ask ? 
Well, go check in our goldbook of statistical tools (*Put ref here*).

Running our t-test, we get a p-value less that $1\cdot10^{-47}$.
This is very small and indeed indicates that the distributions are statistically different.
Thus, winning an oscar makes an impact !

<!-- Oscaro: I knew it ! -->

Let's not stop in a such good path.
Now that we know oscars have an impact, let's estimate it with numbers.
But first, let's be a little careful.

<!-- Oscaro: Why ? -->

Well, you see, humans are very complex and they might not treat all movies the same way, they might be biased.
For instance, maybe that they have nostalgia for older movies and that they will naturally judge them less severly than todays movies (and vice-versa).
Also, not all movies are popular and the number of votes mights influence the ratings. 
We must take that into account.

<!-- Oscaro: Are you sure about that ? Bring me proofs ! -->

You're right to ask, let's check our data !

### Ratings inflation

Let's start with the big picture and check the distributions over the decades.

<div>
  {% include question1/rating_decades_box.html %}
</div>

We already see that something seems to be going on here and that ratings seems to naturally increase over the years.
Now, let's validate this with data !

To do so, we perform an OLS regression of the average ratings on the release year.
This should help us quantify the evolution of ratings over the years.

<div>
  {% include question1/rating_years_scatter.html %}
</div>

The OLS regression yields a coefficient of $0.0085 \pm 0.001$ with a p-value of $0.0$, indicating that the coefficient is statistically significant. This suggests that, on average, a movie's rating increases by $0.0085$ for each more recent release year.

A possible explanation for this trend is that IMDb ratings are relatively recent, with the official website launching in 1990. As a result, the majority of users providing ratings may be more familiar with or emotionally connected to movies released closer to their own time, potentially leading to higher ratings for more recent films.

<!-- Oscaro: Interesting, we need to take that into account ! -->

### Popularity Influence

Another key factor to consider is a movie's popularity, specifically its number of votes. Popular movies are likely to receive higher ratings due to broader exposure and greater audience engagement.

<div>
  {% include question1/scatter_numVotes_vs_averageRating.html %}
</div>

By using a logarithmic scale, we observe that the number of votes and average ratings appear to be correlated in a non-linear way. To verify this relationship, we compute the Spearman correlation, yielding a value of approximately $59.4\%$, supporting the existence of a non-linear association.

To quantify this relationship, we perform an OLS regression of average ratings on the logarithm of the number of votes. The regression yields a coefficient of $0.1826$ with an almost null p-value, indicating statistical significance.

What does this mean in practical terms? It implies that, on average, for every $1\%$ increase in the number of votes, a movie's average rating increases by approximately $0.0018$ units.

<!-- Oscaro: Oh, I see! So the more popular the movie, the better its ratings. Fair enough. -->

Exactly! A possible explanation could be that higher-quality movies tend to receive better ratings, which attract more viewers, ultimately leading to a higher number of votes.

### Final Influence of Winning an Oscar

With a better understanding of potential biases, we can now assess the impact of winning an Oscar on a movie's average rating. We perform an OLS regression using the winner/nominee status as a categorical variable, along with the movie's release year and number of votes as additional predictors.

The regression yields a coefficient of $0.2144$ for winning an Oscar, with a nearly null p-value, indicating strong statistical significance. This suggests that, on average, winning an Oscar in any category increases a movie's average rating by approximately $0.21$ rating points.
