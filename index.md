---
layout: page
title: Oscars of FlOpscars
feature-img: "assets/img/golden_statue.png"
hide: true
---

# Do the Academy Awards Reflect Audience Taste? Oscar's winners vs user's ratings

Are you sad that your favorite movie did not win an Oscar? 

<div class="quote-container">
    <div class="quote-bubble">
        “But it had a very high rating among users, why did this other random movie win?”
        <div class="quote-tail"></div>
    </div>
    <img src="assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

<!--"But it had a very high rating among users, why did this other random movie win?"-->

Look no further! ADA can help us investigate. 

## But what are the Oscars?
It's not your favorite uncle Oscar!

The Oscars are a common name for the Academy Awards. Those award artisic and technical merits in the film industry. 

Fun fact: The origin of the name is disputed but the most famous story is the one of an Academy Awards librarian called Margaret Herrick. When seeing the golden statuette, she exclamed that it reminder her of her Uncle Oscar! 

So it might actually be your favorite uncle Oscar...

Each year, several movies are nominated by the voters in each branch. But in the end, only one movie wins the golden statuette in each category.

### Who votes?
They are voted by the Academy's voting membership. This membership is divided into different branches. Each branch represents a different discipline in film production. Thus actors vote for actors, directors for directors and so on. 

<!--Maybe cite an award ceremony where nobody understood why a movie won and say that ADA can help us investigate → Nomadland (imo (soph) il était nul), maybe also cite some nominated movies that were not liked (like Once upon a time in Hollywood or why The Grand Budapest Hotel didn’t win in 2015 or like why Barbie didn’t win against Oppenheimer)

Explain what the Academy awards are, fun fact about uncle oscar

Explain nominees vs winners
-->


In this story, we will see if there is a big difference between the people's ratings and Oscar awards. We will also see if there is a recipe to success among the Academy Awards.

* * *

## Do Oscar-winning films generally have higher ratings compared to non-winning nominees and top box-office hits?  (Q1)

So, do you think that if your favorite movie gets an oscar, it will get to the top ratings ? 
Well, let's find out !
But before going deep into the analysis, let's start simple, let's see how the ratings are distributed between oscar winners and nominees.
Interesting, we see that the winners seems to have a higher ratings. 

<div>
  {% include question1/boxplot.html %}
</div>


<div class="quote-container">
    <div class="quote-bubble">
        “Nice ! So we are done, winning an oscar will get you to the top !”
        <div class="quote-tail"></div>
    </div>
    <img src="assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

Well well, not that fast. While those results are encouraging, we still need to see if they are significant !

<div class="quote-container">
    <div class="quote-bubble">
        “But how ?”
        <div class="quote-tail"></div>
    </div>
    <img src="assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

To do so, we'll use a simple t-test and see if the distribution are different. What's a t-test you ask ? Well, go check in our goldbook of statistical tools (*Put ref here*).



<h3>Interactive Plot example</h3>

<div id="plotly-chart"></div>

<script type="text/javascript">
  var trace1 = {
    x: [1, 2, 3, 4],
    y: [10, 11, 12, 13],
    mode: 'lines',
    name: 'Test Line'
  };

  var data = [trace1];

  var layout = {
    title: 'Simple Plotly Example',
    xaxis: {
      title: 'X Axis'
    },
    yaxis: {
      title: 'Y Axis'
    }
  };

  Plotly.newPlot('plotly-chart', data, layout);
</script>

* * *

## Are there discernible biases within Oscar winners, such as genre, nationality, or star power, that differ from audience preferences? (Q6)

We know that the Academy Awards are USA-centric. 

### What does it take to be nominated as best picture?

* * *

## Is there a correlation between high-profile actors/directors and Oscar wins, regardless of ratings? (Q3)

<div class="quote-container">
    <div class="quote-bubble">
        "OMG Steven Spielberg directed this movie, it must be a nice one!"
        <div class="quote-tail"></div>
    </div>
    <img src="assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>


Do you really need to make a great movie if Leonardo Di Caprio plays in it? Or if Quentin Tarantino directed it? Let's see if the jury is biased towards some members!


* * *


## How do ratings of Oscar-winning films evolve over time? (Q2)

Does a winner movie age well, like your favourite wine, with the audience?

We will see how the sentiment of the reviews evolves over the time.

### Data collection

To obtain the data and the sentiment of the reviews, we have scraped the IMDB reviews of each movie nominated to the Oscars in the category Best Picture. 

We then performed a sentiment analysis on those using the library *vader*. 

* * *

## Does winning an Oscar lead to a measurable increase in ratings or review counts (i.e., the "Oscar bump")? (Q5)

Have you ever heard of the Oscar bump? It is the increase of the box office performance that a film experiences after receiving an Oscar. 

How does winning an Oscar affect the perceiveness of a movie?

Does the overall sentiment improves after the winning, are people two-faced and start to like a movie only because it won an Oscar?



* * *

## Conclusion


