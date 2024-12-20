
<div class="quote-container">
    <div class="quote-bubble">
        "I always see the same faces at the ceremony, the jury is for sure biased!"
        <div class="quote-tail"></div>
    </div>
    <img src="assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>


Not too fast Oscaro, we will analyze this question using data.
To estimate how popular someone was at the year of the given oscar ceremony, we set a 'high profile score' as the mean of all the box office revenue the person has participated in before the oscar ceremony. Let's start with directors.

<h3> Directors </h3>

As a quick check, do we see the same names when displaying the directors with the highest profile score and the ones that won the most Oscar ?


<div class="plot-container">
  {% include question3/director_interactive.html %}
</div>

<div style="width: 100%; display: flex; justify-content: center; margin-top: 20px; margin-bottom: -10px; padding: 0;">
  <iframe 
    src="question3_plots/count_won_oscar.png" 
    style="width: 100%; max-width: 800px; height: 500px; border: none; margin:0 ; padding: 0;"
    scrolling="no">
    Your browser does not support PNGs. 
    <a href="question3_plots/count_won_oscar.png">Download the PNG</a>.
  </iframe>
</div>

<br>

As we can see, we do not observe any name in common but it is too early to draw any conclusion.


<div class="quote-container">
    <div class="quote-bubble">
        "Exactly, I'm sure that we will find a bias!"
        <div class="quote-tail"></div>
    </div>
    <img src="assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>


Let's do some further analysis.

<br>

If each year, we sort the nominees by average ratings and by 'high profile score' in descending order, we see that the distributions are quite similar and heavy-tailed: Oscar winning-movies are thus well rated and directed by a popular director.

<br>

<div style="width: 100%; display: flex; justify-content: center; margin-top: 20px; margin-bottom: -10px; padding: 0;">
  <iframe 
    src="question3_plots/winner_position.png" 
    style="width: 100%; max-width: 800px; height: 500px; border: none; margin: 0; padding: 0;"
    scrolling="no">
    Your browser does not support PNGs. 
    <a href="question3_plots/winner_position.png">Download the PNG</a>.
  </iframe>
</div>

<br>

To reinforce our intuition, we can perform a statistical test to decide whether there is a significant difference between these 2 distributions. A p-value of \(0.28\) indeed shows that these two metrics are correlated.

<div class="quote-container">
    <div class="quote-bubble">
        "Nice statistical black box method, but there are obviously way less Oscar-winning movies than there are movies overall. What if you take this into account?"
        <div class="quote-tail"></div>
    </div>
    <img src="assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

Nice catch! If only there was a statistical method that could prevent that... Let's see in our ADA toolbox... Propensity score matching could help! Let's use it!

<br>

We will restrict our analysis by matching winning Oscar and non-winning Oscar movies together. This matching aims at connecting two movies with similar director profile score.

<br>

<div style="width: 100%; display: flex; justify-content: center; margin-top: 20px; margin-bottom: -10px; padding: 0;">
  <iframe 
    src="question3_plots/match_and_plot.png" 
    style="width: 100%; max-width: 800px; height: 500px; border: none; margin: 0; padding: 0;"
    scrolling="no">
    Your browser does not support PNGs. 
    <a href="question3_plots/match_and_plot.png">Download the PNG</a>.
  </iframe>
</div>

<br>

On average the Oscar-winning movies get an average rating of \(7.91\), while the other nominated movies get an average rating of \(7.55\). Moreover, the mean difference between each pair of movie with similar profile score is \(0.25\). Thus, at similar profile score, movies that won an oscar get \(0.25\) higher rating.

<div class="quote-container">
    <div class="quote-bubble">
        "OK, you got me this time, but what about actors?"
        <div class="quote-tail"></div>
    </div>
    <img src="assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>


<h3> Actors </h3>

We will now conduct the same analysis steps but for actors. We could expect to see an inverse phenomenon: the audience might be biased towards their favorite actors and give good ratings even if the jury does not consider that the movie deserves an oscar. In fact, an actor is more prone to familiarize an audience as he directly appears in the movie and generates more emotion.

<br>

<div style="width: 100%; display: flex; justify-content: center; margin-top: 20px; margin-bottom: -10px; padding: 0;">
  <iframe 
    src="question3_plots/top_actors.png" 
    style="width: 100%; max-width: 800px; height: 500px; border: none; margin:0px; padding: 0;"
    scrolling="no">
    Your browser does not support PNGs. 
    <a href="question3_plots/top_actors.png">Download the PNG</a>.
  </iframe>
</div>

<div style="width: 100%; display: flex; justify-content: center; margin-top: 20px; margin-bottom: -10px; padding: 0;">
  <iframe 
    src="question3_plots/count_won_oscar_actor.png" 
    style="width: 100%; max-width: 800px; height: 500px; border: none; margin: 0; padding: 0;"
    scrolling="no">
    Your browser does not support PNGs. 
    <a href="question3_plots/count_won_oscar_actor.png">Download the PNG</a>.
  </iframe>
</div>

<br>

Again, no name in common... What about the ranking ?

<br>

<div style="width: 100%; display: flex; justify-content: center; margin-top: 20px; margin-bottom: -10px; padding: 0;">
  <iframe 
    src="question3_plots/winner_position_actors.png" 
    style="width: 100%; max-width: 800px; height: 500px; border: none; margin: 0; padding: 0;"
    scrolling="no">
    Your browser does not support PNGs. 
    <a href="question3_plots/winner_position_actors.png">Download the PNG</a>.
  </iframe>
</div>

<br>

This time, we get a p-value of \(0.47\). It is even higher than with directors. This mean that our profile score, based on revenue and the ratings are even more correlated.

<br>

Last but not least, what do we observe after performing our propensity score matching?

<br>

<div style="width: 100%; display: flex; justify-content: center; margin-top: 20px; margin-bottom: -10px; padding: 0;">
  <iframe 
    src="question3_plots/match_and_plot_actor.png" 
    style="width: 100%; max-width: 800px; height: 500px; border: none; margin: 0; padding: 0;"
    scrolling="no">
    Your browser does not support PNGs. 
    <a href="question3_plots/match_and_plot_actor.png">Download the PNG</a>.
  </iframe>
</div>

<br>

This time, we get a p-value of \(0.066\). Despite being low, it showcases that the distribution are similar as we can see on the plot. This could indicate a slight bias on the side of the audience: the lack of difference highlights that the jury is able to draw a difference between a movie that deserves an oscar and movies that do not but the audience does not as people can give a good rating just because an actor that they like played in the movie.

<br>

We were looking for a bias in the jury but instead, it seems like we found a bias in the audience!


<h3> Bias towards nomination </h3>


<div class="quote-container">
    <div class="quote-bubble">
        "Damn what a plot twist, you should make a movie out of this, it might win you an Oscar! But wait, the jury who nominates is the same as the one who decides who wins the Oscar, so what if the jury's bias was already present in the nomination?"
        <div class="quote-tail"></div>
    </div>
    <img src="assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

Very good remark golden boy, let's find out for both directors and actors!

<br>

<div style="width: 100%; display: flex; justify-content: center; margin-top: 20px; margin-bottom: -10px; padding: 0;">
  <iframe 
    src="question3_plots/match_and_plot_nominated.png" 
    style="width: 100%; max-width: 800px; height: 500px; border: none; margin: 0; padding: 0;"
    scrolling="no">
    Your browser does not support PNGs. 
    <a href="question3_plots/match_and_plot_nominated.png">Download the PNG</a>.
  </iframe>
</div>


<div style="width: 100%; display: flex; justify-content: center; margin-top: 20px; margin-bottom: -10px; padding: 0;">
  <iframe 
    src="question3_plots/match_and_plot_nominated_actor.png" 
    style="width: 100%; max-width: 800px; height: 500px; border: none; margin: 0; padding: 0;"
    scrolling="no">
    Your browser does not support PNGs. 
    <a href="question3_plots/match_and_plot_nominated_actor.png">Download the PNG</a>.
  </iframe>
</div>

<br>

After matching on both actors and directors, we see that, even with similar profile scores, the movies that are not nominated have lower ratings on average. This gap is more pronounced than the one we observed among the nominated movies as the average difference between two pairs is 1.13

<br>

This confirms that the jury is not biased for both nominating and choosing the winner


<div class="quote-container">
    <div class="quote-bubble">
        "I guess I'll agree with the data supremacy..."
        <div class="quote-tail"></div>
    </div>
    <img src="assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>