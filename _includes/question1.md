
So, do you think that if your favorite movie gets an oscar, it will get to the top ratings ? 
Well, let's find out !
But before going deep into the analysis, let's start simple, let's see how the ratings are distributed between oscar winners and nominees.


<div class="plot-container">
  {% include question1/boxplot.html %}
</div>


Interesting, we see that the winners seems to have a higher ratings.

<div class="quote-container">
    <div class="quote-bubble">
        “Nice ! So we are done, winning me will get you to the top !”
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>



Well well, not that fast. While those results are encouraging, we still need to see if they are significant !
To do so, we'll use a simple t-test and see if the distribution are different. What's a t-test you ask ? 
Well, go check in our goldbook of statistical tools (*Put ref here*).
<!-- On peut éventuellement faire ue sorte de "libre d'or" de nos méthodes stats, mais à voir avec les autres -->

Running our t-test, we get a p-value less than \(1\cdot10^{-47}\).
This is very small and indeed indicates that the distributions are statistically different.
Thus, winning an oscar makes an impact !

<div class="quote-container">
    <div class="quote-bubble">
        “I knew it !”
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>


Let's not stop in a such good path.
Now that we know oscars have an impact, let's estimate it with numbers.
But first, let's be a little careful.


<div class="quote-container">
    <div class="quote-bubble">
        “Why ?”
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

Well, you see, humans are very complex creatures and they might not treat all movies the same way, they might be biased.
For instance, maybe that they have nostalgia for older movies and that they will naturally judge them less severly than todays movies (and vice-versa).
Also, not all movies are popular and the number of votes mights influence the ratings. 
We must take that into account.


<div class="quote-container">
    <div class="quote-bubble">
        “Are you sure about that ? Bring me proofs !”
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

You're right to ask, let's check our data !

<hr>

<h3> Ratings inflation </h3>

Let's start with the big picture and check the distributions over the decades.


<div class="plot-container">
  {% include question1/rating_decades_box.html %}
</div>


We already see that something seems to be going on here and that ratings seems to naturally increase over the years.
Now, let's validate this with data !

To do so, we perform an OLS regression of the average ratings on the release year.
This should help us quantify the evolution of ratings over the years.


<div class="plot-container">
  {% include question1/rating_years_scatter.html %}
</div>


The OLS regression yields a coefficient of \(0.0085 \pm 0.001\) with a p-value of \(0.0\), indicating that the coefficient is statistically significant. This suggests that, on average, a movie's rating increases by \(0.0085\) for each more recent release year.

A possible explanation for this trend is that IMDb ratings are relatively recent, with the official website launching in 1990. As a result, the majority of users providing ratings may be more familiar with or emotionally connected to movies released closer to their own time, potentially leading to higher ratings for more recent films.


<div class="quote-container">
    <div class="quote-bubble">
        “Interesting, we need to take that into account !”
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

<hr>

<h3> Popularity Influence </h3>

Another key factor to consider is a movie's popularity, specifically its number of votes. Popular movies are likely to receive higher ratings due to broader exposure and greater audience engagement.


<div class="plot-container">
  {% include question1/scatter_numVotes_vs_averageRating.html %}
</div>


By using a logarithmic scale, we observe that the number of votes and average ratings appear to be correlated in a non-linear way. To verify this relationship, we compute the Spearman correlation, yielding a value of approximately \(59.4\%\), supporting the existence of a non-linear association.

To quantify this relationship, we perform an OLS regression of average ratings on the logarithm of the number of votes. The regression yields a coefficient of \(0.1826\) with an almost null p-value, indicating statistical significance.

What does this mean in practical terms? It implies that, on average, for every \(1\%\) increase in the number of votes, a movie's average rating increases by approximately \(0.0018\) units.


<div class="quote-container">
    <div class="quote-bubble">
        “Oh, I see! So the more popular the movie, the better its ratings. Fair enough.”
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

Exactly! A possible explanation could be that higher-quality movies tend to receive better ratings, which attract more viewers, ultimately leading to a higher number of votes.

<hr>

<h3> Final Influence of Winning an Oscar </h3>

With a better understanding of potential biases, we can now assess the impact of winning an Oscar on a movie's average rating. We perform an OLS regression using the winner/nominee status as a categorical variable, along with the movie's release year and number of votes as additional predictors.

The regression yields a coefficient of \(0.2144\) for winning an Oscar, with a nearly null p-value, indicating strong statistical significance. This suggests that, on average, winning an Oscar in any category increases a movie's average rating by approximately \(0.21\) rating points.

<hr>

<h3> Ratings and Number of Oscars </h3>

Let’s explore the relationship between the number of Oscars won and average ratings. Intuitively, winning more Oscars should correlate with higher ratings. Let's check that.


<div class="plot-container"> {% include question1/nb_oscars_boxplot.html %} </div>


As expected, the results confirm this trend: movies with more Oscars tend to have higher average ratings.

An interesting observation is that only one movie has ever won 11 Oscars—Titanic, which still holds the record for the most Oscars won by a single film.

<div style="width: 100%; display: flex; justify-content: center; margin-top: 20px; margin-bottom: -10px; padding: 0;">
  <iframe 
    src="{{ site.baseurl }}/assets/img/titanic.png" 
    style="width: 100%; max-width: 800px; height: 500px; border: none; margin: 0; padding: 0;"
    scrolling="no">
    Your browser does not support PNGs. 
    <a href="{{ site.baseurl }}/assets/img/titanix.png">Download the PNG</a>.
  </iframe>
</div>

<div class="quote-container">
    <div class="quote-bubble">
        “Yeah, I remember that movie... I cried so much !”
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

<hr>

<h3> Causal effect per category </h3>

Not all Oscar categories carry the same weight. Winning in Special Effects or Actor, for instance, likely has a different impact on average ratings.

<div class="quote-container">
    <div class="quote-bubble">
        “That's right, I have so many categories. How are we going to figure that out ?”
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

Let’s start simple and see if we can extract meaningful insights. Our approach is as follows: for each category, we construct a bipartite graph connecting nominees (control group) and winners (treated group). We link nominees and winners if their movies were released in the same year. Each edge is weighted by the difference in the number of votes. We then find pairings that minimize the vote difference, allowing us to estimate a meaningful causal effect.

<div class="quote-container">
    <div class="quote-bubble">
        “That's it?”
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

Not quite. A few additional considerations are essential:

- To ensure robust results, we require a minimum of 10 pairs per category.
- If a movie wins an Oscar in one category but is only nominated in another, we exclude it from the nominee group to avoid bias.
- To isolate the effect of winning a single Oscar in one category, we remove movies that have won multiple Oscars.

With these constraints, we narrow down to a select few categories where causal effects can be reliably calculated.


<div class="plot-container"> {% include question1/raw_causal_effects_bar.html %} </div>


Despite these limitations, the results are already revealing. For example, winning an Oscar in Special Effects appears to have the largest impact on average ratings, with an Average Treatment Effect (ATE) of approximately \(0.53\).

<div class="quote-container">
    <div class="quote-bubble">
        “Hmm, that’s nice, but couldn’t we do better? I have multiple categories that are quite similar. Couldn’t we group them to get more data ?”
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

<hr>

<h3> Clustering the categories </h3>

Great idea! Our dataset contains 59 categories with at least 10 entries, and some of them are indeed similar. For example, we could group the Actor and Actress categories under a broader Acting category. By pooling data, we could compute more robust causal effects.

To achieve this, we apply the k-means algorithm. First, we embed the categories into vectors and then perform clustering. Given the relatively small sample size (59), we manually select the optimal number of clusters, determining it to be \(k_{optimal} = 12\).

<br>

While k-means provides a strong foundation, some adjustments are needed. Thanks to the small number of samples, we fine-tune the clusters through manual inspection to ensure the clusters are coherent.

<div class="quote-container">
    <div class="quote-bubble">
        “That sounds great ! But how can I check if the groups are good visually ?”
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

Good question! We visualize the clusters by reducing the embedded vectors to two or three dimensions using Principal Component Analysis (PCA). This allows us to see how well the categories group together.

<br>

Here’s a 2D and 3D visualization of the clusters:


<div class="side-by-side-plots">
  <div class="plot-container">
    {% include question1/clusters_2d.html %}
  </div>

  <div class="plot-container">
    {% include question1/clusters_3d.html %}
  </div>
</div>


It’s worth noting that clusters might look scrambled in these graphs. This is because k-means clustering was performed in the higher-dimensional space, and dimensionality reduction can distort the visual representation. Rest assured, the clusters remain valid in their original space.

<hr>

<h3> Causal effect per category - revisited </h3>

With broader categories established, we can perform a similar causal analysis. Here are the updated results:


<div class="plot-container"> {% include question1/new_causal_effects_bar.html %} </div>


As expected, Effects remains the most influential category, consistent with our previous findings. Interestingly, we now see that Cinematography and Sound also have a notable impact on average ratings. While Writing has a positive effect, its influence is nearly half that of the top categories.

These insights suggest that audiences seem to value the sensory aspects of movies (visual and sound effects) more than the story itself.

On a side note, we still lack enough samples to estimate a robust causal effect for the Best Picture category. This is because Best Picture wins are rarely standalone and are often accompanied by wins in other categories. Due to our pipeline’s restrictions, we cannot compute a meaningful effect for these cases.


<div class="quote-container">
    <div class="quote-bubble">
        “Interesting. I guess we'll have to further analyze the *Best Picture* category then!”
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>
