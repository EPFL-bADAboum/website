<h4>Distributions for Countries and Genres:</h4>

<div style="width: 100%; display: flex; justify-content: center; gap: 20px; margin-top: 20px; padding: 0;">
  <!-- Plot for countries -->
  <iframe 
    src="{{ site.baseurl }}/question6_plots/countries.png" 
    style="width: 100%; max-width: 800px; height: 500px; border: none; margin: 0; padding: 0;"
    scrolling="no">
    Your browser does not support PNGs. 
    <a href="{{ site.baseurl }}/question6_plots/countries.png">Download the PNG</a>.
  </iframe>

  <!-- Plot for genres -->
  <iframe 
    src="{{ site.baseurl }}/question6_plots/genres.png" 
    style="width: 100%; max-width: 800px; height: 500px; border: none; margin: 0; padding: 0;"
    scrolling="no">
    Your browser does not support PNGs. 
    <a href="{{ site.baseurl }}/question6_plots/genres.png">Download the PNG</a>.
  </iframe>
</div>

<div class="quote-container">
    <div class="quote-bubble">
        "Wow USA and Drama slayed !"
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

<h4> For runtime: </h4>

<div style="width: 100%; display: flex; justify-content: center; margin-top: 20px; margin-bottom: -10px; padding: 0;">
  <iframe 
    src="{{ site.baseurl }}/question6_plots/runtime.png" 
    style="width: 100%; max-width: 800px; height: 500px; border: none; margin:0px; padding: 0;"
    scrolling="no">
    Your browser does not support PNGs. 
    <a href="{{ site.baseurl }}/question6_plots/runtime.png">Download the PNG</a>.
  </iframe>
</div>


Let’s see if the jury has preferences when choosing nominees. For this, we will analyze the genres, countries and runtimes with GLS regression. We only plot the GLS for the significant countries, which have a p-value smaller 0.05.

<div class="quote-container">
    <div class="quote-bubble">
        "Surely the USA are on top !"
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

<div class="plot-container">
  {% include question6/gls_plots.html %}
</div>

<div class="quote-container">
    <div class="quote-bubble">
        "OMG the USA are not there anymore, that means that they don't have a coefficient significant enough! But wow Algeria is so high ? "
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

Algeria's large coefficient is due to its small sample size of only 14 movies, with Z winning an Oscar heavily skewing the results and creating a strong positive association. Frequent collaborations with high-performing countries like France further amplify this influence. Additionally, OLS is highly sensitive to outliers such as Z, which disproportionately inflate Algeria's coefficient.

<br>

<h5> GLS Model Coefficients for runtime: </h5>

<div style="display: flex; justify-content: center; margin-left: 100px;">
  <table style="
    border-collapse: collapse; 
    width: 80%; 
    text-align: center; 
    font-size: 18px;">
    <thead>
      <tr style="background-color: #AEEFF3; color: #000;">
        <th style="border: 1px solid #444; padding: 10px;">Feature</th>
        <th style="border: 1px solid #444; padding: 10px;">Coefficient</th>
        <th style="border: 1px solid #444; padding: 10px;">Std. Error</th>
        <th style="border: 1px solid #444; padding: 10px;">t-value</th>
        <th style="border: 1px solid #444; padding: 10px;">P>|t|</th>
        <th style="border: 1px solid #444; padding: 10px;">95% CI Lower</th>
        <th style="border: 1px solid #444; padding: 10px;">95% CI Upper</th>
      </tr>
    </thead>
    <tbody>
      <tr style="background-color: #E9E9FF; color: #000;">
        <td style="border: 1px solid #444; padding: 10px;">Intercept</td>
        <td style="border: 1px solid #444; padding: 10px;">-0.1708</td>
        <td style="border: 1px solid #444; padding: 10px;">0.006</td>
        <td style="border: 1px solid #444; padding: 10px;">-27.422</td>
        <td style="border: 1px solid #444; padding: 10px;">0</td>
        <td style="border: 1px solid #444; padding: 10px;">-0.183</td>
        <td style="border: 1px solid #444; padding: 10px;">-0.159</td>
      </tr>
      <tr style="background-color: #E9E9FF; color: #000;">
        <td style="border: 1px solid #444; padding: 10px;">Runtime</td>
        <td style="border: 1px solid #444; padding: 10px;">0.0059</td>
        <td style="border: 1px solid #444; padding: 10px;">0.0000524</td>
        <td style="border: 1px solid #444; padding: 10px;">113.215</td>
        <td style="border: 1px solid #444; padding: 10px;">0</td>
        <td style="border: 1px solid #444; padding: 10px;">0.006</td>
        <td style="border: 1px solid #444; padding: 10px;">0.006</td>
      </tr>
    </tbody>
  </table>
</div>



<div class="quote-container">
    <div class="quote-bubble">
        "Nice regressions ! But what can I deduce from this ?"
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

We will highlight the most important coefficients:
<h4> Positive Associations: </h4>

<ul>
  <li> <b>Genres:</b> Drama (+0.4463), Biography (+0.3162), Family (+0.1644) </li>
  <li> <b>Countries:</b> United States (+0.4925), United Kingdom (+0.3249), Algeria (+0.6837) </li>
  <li> <b>Runtime:</b> Each additional minute increases the probability of being nominated slightly (+0.0059)</li>
</ul>

<h4> Negative Associations: </h4>

<ul>
  <li> <b>Genres:</b> Documentary (-0.1194), Action (-0.0601). </li>
  <li> <b>Countries:</b> Vietnam (-0.2915), Canada (-0.1678), Germany (-0.1399) </li>
</ul>

These patterns suggest certain countries, genres, and even longer runtimes have a higher likelihood of producing nominees.

<div class="quote-container">
    <div class="quote-bubble">
        "Oh, so the jury does have some quite specific preferences! I wonder if these are obvious to the point where we can predict the nominations. If so, we might have found the secret recipe for an award winning movie…"
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

You’re right let’s see if we can build a model that predicts accurately the nominations. For this classification task, we will use Logistic Regression. We also add the release year as a feature to see if we can take into account the trends.


<div style="display: flex; justify-content: center; margin: 20px 0;">
  <table style="
    border-collapse: collapse; 
    width: 55%; 
    text-align: center; 
    font-size: 18px; 
    background-color: #2C303A; 
    color: #FFFFFF; 
    margin: 0 auto;">
    <thead>
      <tr>
        <th style="border: 1px solid #444; padding: 10px;">Label</th>
        <th style="border: 1px solid #444; padding: 10px;">Precision</th>
        <th style="border: 1px solid #444; padding: 10px;">Recall</th>
        <th style="border: 1px solid #444; padding: 10px;">F1-Score</th>
        <th style="border: 1px solid #444; padding: 10px;">Support</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td style="border: 1px solid #444; padding: 10px;">False</td>
        <td style="border: 1px solid #444; padding: 10px;">1.00</td>
        <td style="border: 1px solid #444; padding: 10px;">0.91</td>
        <td style="border: 1px solid #444; padding: 10px;">0.95</td>
        <td style="border: 1px solid #444; padding: 10px;">5479</td>
      </tr>
      <tr>
        <td style="border: 1px solid #444; padding: 10px;">True</td>
        <td style="border: 1px solid #444; padding: 10px;">0.07</td>
        <td style="border: 1px solid #444; padding: 10px;">0.67</td>
        <td style="border: 1px solid #444; padding: 10px;">0.13</td>
        <td style="border: 1px solid #444; padding: 10px;">57</td>
      </tr>
    </tbody>
    <tfoot>
      <tr>
        <th colspan="4" style="border: 1px solid #444; padding: 10px; text-align: right;">Accuracy</th>
        <td style="border: 1px solid #444; padding: 10px;">0.91</td>
      </tr>
      <tr>
        <th colspan="4" style="border: 1px solid #444; padding: 10px; text-align: right;">Macro Avg</th>
        <td style="border: 1px solid #444; padding: 10px;">Precision: 0.53, Recall: 0.79, F1-Score: 0.54</td>
      </tr>
      <tr>
        <th colspan="4" style="border: 1px solid #444; padding: 10px; text-align: right;">Weighted Avg</th>
        <td style="border: 1px solid #444; padding: 10px;">Precision: 0.99, Recall: 0.91, F1-Score: 0.94</td>
      </tr>
      <tr>
        <th colspan="4" style="border: 1px solid #444; padding: 10px; text-align: right;">ROC-AUC Score</th>
        <td style="border: 1px solid #444; padding: 10px;">0.8773</td>
      </tr>
    </tfoot>
  </table>
</div>





Unfortunately, it seems that predicting nominations is more difficult than it seems. 

<div class="quote-container">
    <div class="quote-bubble">
        "How come ?"
        <div class="quote-tail"></div>
    </div>
    <img src="{{ site.baseurl }}/assets/img/person.png" alt="Person saying the quote" class="quote-image">
</div>

Well you can see that the precision is very bad, thus making the F1-Score very low.

<br>

Sorry Oscaro, looks like there is no recipe to success…