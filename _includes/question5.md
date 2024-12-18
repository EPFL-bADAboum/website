Have you ever heard of the Oscar bump? It is the increase of the box office performance that a film experiences after receiving an Oscar. 

<br>

How does the public react when a movie is nominated for an Oscar? 

<br>

Does the overall sentiment improves after the winning, are people two-faced and start to like a movie only because it won an Oscar?

<h3> Data collection </h3>
We gathered the IMDb reviews of all the movies nominated for the "Best Picture" award and filtered out the ones that were published too early before the nomination date (more that 2 months before the nomination) and too late after the ceremony date (more that 2 months after the ceremony). This leaves us with reviews published in the short period of time around the "Oscar window" (nomination and ceremony generally 2 months later). Our goal with this particular dataset is to determine if trends in the number or reviews and general opinion emerge from an Oscar nomination. 

<br>

We used the "VaderSentiment" analysis tool in order to compute the "compound score" of each review. A positive review (in terms of words) will have a positive compound score (from 0 to 1) and a negative one will have a negative score (from -1 to 0).

<br>

To start our analysis, let us first visualize the distribution using a Kernel Density Estimate (KDE) plot of the compound score for the reviews published before and after the nomination: 

<br>

<div style="width: 100%; display: flex; justify-content: center; margin-top: 20px; margin-bottom: -10px; padding: 0;">
  <iframe 
    src="{{ site.baseurl }}/question5_plots/Distribution_before_after.png" 
    style="width: 100%; max-width: 800px; height: 500px; border: none; margin: 0; padding: 0;"
    scrolling="no">
    Your browser does not support PNGs. 
    <a href="{{ site.baseurl }}/question5_plots/Distribution_before_after.png">Download the PNG</a>.
  </iframe>
</div>

The plot show that most reviews are either very negative or very positive, with a higher number of positive reviews compared to negative ones. 

<br>

People seem to have very polarized opinions. A movie is either a masterpiece or complete garbage! We can see an example of a very bad review and a very good one for the silent movie The Artist produced by Thomas Langmann and starring Jean Dujardin in 2011. It won the Best Picture Award. 

<br>

<div style="display: flex; justify-content: center; width: 100%; align-items: center;">

  <!-- Left arrow (disabled initially if the first image is visible) -->
  <button id="leftArrow" onclick="showImage(0)" 
    style="background-color: transparent; border: none; cursor: pointer; font-size: 2em; margin-right: 10px; opacity: 0.5;">
    &#8592;
  </button>

  <!-- Image container with a fixed size -->
  <div style="display: flex; flex-direction: column; align-items: center; width: 800px; height: 350px; overflow: hidden; padding: 10px; margin-top: 0px">
    <img id="image1" src="{{ site.baseurl }}/question5_plots/good_rev_artist.png" style="width: 100%; height: 100%; object-fit: contain; display: block;">
    <img id="image2" src="{{ site.baseurl }}/question5_plots/bad_rev_artist.png" style="width: 100%; height: 100%; object-fit: contain; display: none;">
  </div>

  <!-- Right arrow (disabled initially if the second image is visible) -->
  <button id="rightArrow" onclick="showImage(1)" 
    style="background-color: transparent; border: none; cursor: pointer; font-size: 2em; margin-left: 10px; opacity: 1;">
    &#8594;
  </button>
</div>


<script>
  // Function to toggle between the two images
  function showImage(imageIndex) {
    var image1 = document.getElementById('image1');
    var image2 = document.getElementById('image2');
    var leftArrow = document.getElementById('leftArrow');
    var rightArrow = document.getElementById('rightArrow');
    
    if (imageIndex === 0) {
      image1.style.display = 'block';
      image2.style.display = 'none';
      leftArrow.style.opacity = 0;  // Disable the left arrow when on the first image
      rightArrow.style.opacity = 1;  // Enable the right arrow
    } else {
      image1.style.display = 'none';
      image2.style.display = 'block';
      leftArrow.style.opacity = 1;   // Enable the left arrow
      rightArrow.style.opacity = 0;  // Disable the right arrow when on the second image
    }
  }

  // Initialize with the first image visible and disable the left arrow
  window.onload = function() {
    showImage(0);  // Start with the first image
  };
</script>


<br>



<div class="quote-container">
    <div class="quote-bubble">
        “What an interesting finding, it seems that the distribution does not change before and after the nomination. People are probably not two-faced !”
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

Yes that is interesting. But is it really the same? Let's see what we can use from our statistics toolbox.

<br>

Let's perform a Kolmogorov-Smirnov test and see the p-value. If it is lower than \(0.05\) it means that we can reject the fact that the distributions are not different. 

<br>

With this test, we obtain a p-value of \(0.002\) which means that we reject the null hypothesis! So the distributions are in fact not the same...

<div class="quote-container">
    <div class="quote-bubble">
        “Wow, how does it change then?”
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

To see the difference in the compound score further, we train several regression models using the compound scores from positive, negative, and global reviews, both before and after the nomination. The goal of this analysis is to assess whether there is a significant shift in the mean of the scores before and after this event, and what it looks like. 


<br>

<div style="display: flex; justify-content: center; margin: 20px 0;">
  <table style="
    border-collapse: collapse; 
    width: 60%; 
    text-align: center;
    font-size: 25px;">
    <thead>
      <tr style="background-color: #2C303A; color: #FFFFFF;">
        <th style="border: 1px solid #444; padding: 10px;"> </th>
        <th style="border: 1px solid #444; padding: 10px;">P-value</th>
        <th style="border: 1px solid #444; padding: 10px;">Score shift after nomination</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <th style="border: 1px solid #444; padding: 10px;">Positive</th>
        <td style="border: 1px solid #444; padding: 10px;">0.304</td>
        <td style="border: 1px solid #444; padding: 10px;">0.001</td>
      </tr>
      <tr>
        <th style="border: 1px solid #444; padding: 10px;">Negative</th>
        <td style="border: 1px solid #444; padding: 10px;">0.735</td>
        <td style="border: 1px solid #444; padding: 10px;">-0.011</td>
      </tr>
      <tr>
        <th style="border: 1px solid #444; padding: 10px;">Overall</th>
        <td style="border: 1px solid #444; padding: 10px;">0.0</td>
        <td style="border: 1px solid #444; padding: 10px;">-0.036</td>
      </tr>
    </tbody>
  </table>
</div>

<div class="quote-container">
    <div class="quote-bubble">
        “What do all those value mean?”
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

<h4> Positive case </h4>
Based on the positive regression, we can see that the change in positive scores is not significant (P-Value > 0.05). This suggests that the positive reviews after the nomination remain just as positive as they were before. Moreover, there is only a shift of 0.001 in the score after the nomination.

<br>

<h4> Negative case </h4>
Like in the case of the positive reviews, we can observe that the change in negative scores is not significant (P-Value > 0.05). This suggests that the negative reviews after the nomination remain just as negative as they were before. Furthermore, there is only a shift of -0.011 in the score after the nomination.

<br>

<h4> Overall case </h4>
When considering all reviews (both positive and negative), the resulting p-value of the regression is very small (p < 0.05). This indicates that compound scores significantly decreased after the nomination.

<br>

From the two previous tests, we know that the positive and negative compound scores do not change. A plausible explanation for this result could be that a higher number of negative reviews and/or fewer positive reviews are published after the nomination. This shift in review composition lowers the mean compound score, which in this case is -0.036.


<br>

<div class="quote-container">
    <div class="quote-bubble">
        “So people actually becore more salty !”
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>


<p>To better understand this phenomenon, let's plot the distributions of the compound scores under different conditions:</p>

<ul>
  <li>Neutral: Compound score < 0.2</li>
  <li>Positive: Compound score > 0.2</li>
  <li>Really positive: Compound score > 0.8</li>
</ul>
Note: The same thresholds apply to classify negative reviews.


<div class="plot-container"> {% include question5/compound_score_distrib.html %} </div>

<div class="quote-container">
    <div class="quote-bubble">
        “What can I see here ?”
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

So in the plot above, you can see the differences of distribution in various scenarios.

<br>

We observe that each major event (nomination and ceremony) results in an increase in the number of negative reviews. This effect is more pronounced in the case of the nomination.

<div class="quote-container">
    <div class="quote-bubble">
        “So actually, winning an Oscar reduces the rating !”
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

Well Oscar-winning movies are more likely to experience a change in the average compound score. This shift could be attributed to the heightened attention and discussion generated by their success.

<br>

The Winners vs Losers reveals that winning movies receive a higher proportion of "Really Positive" reviews and fewer "Really Negative" ones. Interestingly, these movies do not show a larger proportion of "Positive" reviews. This suggests that the positive feedback is more "extreme," with reviewers strongly emphasizing the quality of the winning films.


<br>

Winning an Oscar often draws a more polarized response from viewers, leading to a measurable impact on the compound score. On the other side, losing movies tend to maintain more stable compound scores, possibly because they lack the same surge of public interest.

<div class="quote-container">
    <div class="quote-bubble">
        “Can we see how does the rating evolve over time ?”
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

Sure! We will visualize how the compound scores and review counts evolve over time. By plotting these two metrics on a timeline, we can better understand the dynamics of the audience engagement during key events, such as nominations and awards ceremonies.

<br>

The time 0 is the ceremony date and -60 is around the nomination date.


<div class="plot-container"> {% include question5/timeseries.html %} </div>

A clear trend emerges where the mean compound score of nominated movies worsens over time. In other words, the number of negative reviews increases, which aligns with the often critical nature of online websites. It seems that as movies gain more visibility, they also attract more "haters."

<br>

We also observe that the number of reviews drops sharply after the ceremony. The hype appears to peak between the nomination and the ceremony, with one final surge in activity immediately following the awards. After this brief post-ceremony spike, engagement rapidly declines, suggesting that public interest fades quickly once the event is over.

<br>