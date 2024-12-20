---
layout: page
title: Oscars or FlOpscars
feature-img: "assets/img/golden_statue.png"
hide: true
---

# Do the Academy Awards Reflect Audience Taste? Oscar winners vs users' ratings

Are you sad that your favorite movie did not win an Oscar?

<div class="quote-container">
    <div class="quote-bubble">
        “But it had a very high rating among users, why did this other random movie win?”
        <div class="quote-tail"></div>
    </div>
    <img src="assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

Look no further! ADA can help us investigate.

## But what are the Oscars?

It's not your favorite uncle Oscar!

The Oscars are a common name for the Academy Awards. Those award artisic and technical merits in the film industry.

Fun fact: The origin of the name is disputed but the most famous story is the one of an Academy Awards librarian called Margaret Herrick. When seeing the golden statuette, she exclamed that it reminder her of her Uncle Oscar!

So it might actually be your favorite uncle Oscar...

### Who votes?

They are voted by the Academy's Voting Membership. This membership is divided into different branches. Each branch represents a different discipline in film production.

Every year, several movies are nominated by the voters in each branch. Thus actors nominate for actors, directors for directors and so on. But in the end, only one movie wins the golden statuette in each category. However, the Best Picture category is the most general one, as every member nominates their favorite movies.

All active members in the Academy can vote for all of the categories. They must rank the nominated movies in their preferential order. The movie that gets 50 percent or more of the votes is the winner.

In this story, we will see if there is a big difference between the people's ratings and Oscar awards. We will also see if there is a recipe to success among the Academy Awards.

## The data we have

The data we are working on comes from several datasets:

- The CMU dataset
- The IMDB dataset
- Oscar winners and nominees for each year

Throughout this story, we will consider IMDB ratings which range from 1 to 10.

---

## Do Oscar-winning films generally have higher ratings compared to non-winning nominees ?

<div>
  {% include question1.md %}
</div>

---
## Does winning an Oscar lead to a measurable increase in ratings or review counts (i.e., the "Oscar bump")?

<div class="quote-container">
    <div class="quote-bubble">
        "I'm sure that people only like a movie because it won an Oscar!"
        <div class="quote-tail"></div>
    </div>
    <img src="assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

Well my friend, let's see.

<div>
  {% include question5.md %}
</div>

<hr>

## Are there discernible biases within Oscar winners, such as genre, nationality, or star power, that differ from audience preferences?

However as we have seen in the introduction, the nomination and voting is done by the same members. Thus the critic's bias may already be in the nomination. We will now compare the nominated movies with movies that were not.

<div>
  {% include question6.md %}
</div>

---

## Is there a correlation between high-profile actors/directors and Oscar wins, regardless of ratings?

<div class="quote-container">
    <div class="quote-bubble">
        "OMG Steven Spielberg directed this movie, it must be a nice one!"
        <div class="quote-tail"></div>
    </div>
    <img src="assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

Do you really need to make a great movie if Leonardo Di Caprio plays in it? Or if Quentin Tarantino directed it? Let's see if the jury is biased towards some members!

<div>
  {% include question3.md %}
</div>

---

<h2> How do ratings of Oscar-winning films evolve over time? </h2>

Does a winner movie age well, like your favourite wine, with the audience?

We will see how the sentiment of the reviews evolves over the time after the Oscar ceremony. Is there a noticeable "hype effect" surrounding the awards?

<div>
  {% include question2.md %}
</div>

<hr>

<h2> Conclusion </h2>

In the end, the Oscars don’t just reflect audience taste, they shape it in subtle ways. Winning an Oscar nudges a movie’s ratings upward, and certain categories like Special Effects give an even bigger punch. But it’s not so simple: ratings naturally drift higher over time as audience biases shift, and popular films do well regardless of awards. Around nominations and the ceremony, hype surges and opinions polarize, but this excitement gradually fades, with even winners eventually blending back into the broader cinematic landscape. The Oscars guide where people look, but in the long run, the audience still carves its own path, reminding us that what truly lasts in cinema isn’t just who takes home the statuette, but who keeps winning over our hearts.

Oscaro and the bADAboum team wish you happy holidays!

<div class="quote-container">
    <div class="quote-bubble">
        "Cheers !"
        <div class="quote-tail"></div>
    </div>
    <img src="assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>
