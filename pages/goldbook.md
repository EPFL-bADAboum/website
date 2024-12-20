---
layout: page
title: Statistical GoldBook
permalink: /goldbook/
---

# Statistical GoldBook

## Pearson correlation

<div class="stat-item">
  <div class="stat-text">
    This allows to measure the linear relationship between two continuous variables. It ranges from -1 to 1, and indicates the direction and strength of the association.
  </div>
  <div class="stat-image">
    <img src="/assets/img/goldbook/pearson_correlation.png" alt="Pearson Correlation Example">
    <figcaption>[Example of Pearson correlations](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient)</figcaption>
  </div>
</div>

## Spearman Correlation

<div class="stat-item">
  <div class="stat-text">
    It measures how well two variables are related by ranking their values. If one variable consistently increases or decreases as the other changes, they have a strong Spearman correlation. It works even if the relationship is not linear, making it useful when data isn’t normally distributed or has outliers. This makes this tool particularly useful when we suspect a non-linear relationship.
  </div>
  <div class="stat-image">
    <img src="/assets/img/goldbook/spearman_correlation.png" alt="Spearman Correlation Example">
    <figcaption>Source: [Add Source Here]</figcaption>
  </div>
</div>

## T-test

<div class="stat-item">
  <div class="stat-text">
    It checks if the averages (means) of two groups are significantly different from each other. It works by comparing the difference between the group means relative to the variation within the groups. If the difference is large compared to the variation, the t-test suggests that the groups are likely different. This tests assumes the data is roughly normaly distributed.
  </div>
  <div class="stat-image">
    <img src="/assets/img/goldbook/t_test.png" alt="T-test Example">
    <figcaption>Source: [Add Source Here]</figcaption>
  </div>
</div>

## Kolmogorov-Smirnov Test

<div class="stat-item">
  <div class="stat-text">
    The Kolmogorov-Smirnov (KS) test compares two datasets to see if they come from the same distribution. It looks at the biggest difference between their cumulative distributions. If this difference is large, the test suggests the datasets are from different populations. The KS test works with any type of continuous data and doesn’t assume a specific distribution. This makes it useful for checking the conformity of our data.
  </div>
  <div class="stat-image">
    <img src="/assets/img/goldbook/kolmogorov_smirnov.png" alt="Kolmogorov-Smirnov Test Example">
    <figcaption>Source: [Add Source Here]</figcaption>
  </div>
</div>

## OLS (Ordinary Least Square) Regression

<div class="stat-item">
  <div class="stat-text">
    This regression finds the best-fitting line through data points by minimizing the distance between observed and predicted values. It works by adjusting the line to reduce the sum of squared errors. It assumes a linear relationship, constant variance of errors, and normally distributed residuals.
  </div>
  <div class="stat-image">
    <img src="/assets/img/goldbook/ols_regression.png" alt="OLS Regression Example">
    <figcaption>Source: [Add Source Here]</figcaption>
  </div>
</div>

## GLS (Generalized Least Squares)

<div class="stat-item">
  <div class="stat-text">
    This model extends OLS by handling situations where data points have different variances or are correlated. It adjusts the model to account for these issues and gives more accurate estimates. It is particularly useful in time series, where observations are often dependent or have unequal variability.
  </div>
  <div class="stat-image">
    <img src="/assets/img/goldbook/gls_regression.png" alt="GLS Example">
    <figcaption>Source: [Add Source Here]</figcaption>
  </div>
</div>

## Logistic Regression

<div class="stat-item">
  <div class="stat-text">
    Logistic regression predicts binary outcomes (e.g., success/failure) instead of continuous values like OLS. It estimates the probability of an event using a logistic curve, producing results between 0 and 1. It is very useful for classification tasks.
  </div>
  <div class="stat-image">
    <img src="/assets/img/goldbook/logistic_regression.png" alt="Logistic Regression Example">
    <figcaption>Source: [Add Source Here]</figcaption>
  </div>
</div>

## Propensity Score Matching

<div class="stat-item">
  <div class="stat-text">
    This method pairs individuals from two groups (e.g., treated and control) based on similar characteristics. It first calculates a score that predicts the likelihood of being in one group based on observed variables. By matching individuals with similar scores, we create comparable groups and reduce the bias when estimating the treatment effects.
  </div>
  <div class="stat-image">
    <img src="/assets/img/goldbook/propensity_score_matching.png" alt="Propensity Score Matching Example">
    <figcaption>Source: [Add Source Here]</figcaption>
  </div>
</div>

## Principal Component Analysis (PCA)

<div class="stat-item">
  <div class="stat-text">
    This method reduces the number of dimensions by combining variables that explain the most variance in the data. The first principal component captures the largest amount of variance, followed by the second, and so on. This simplifies the dataset while preserving its most important information.
  </div>
  <div class="stat-image">
    <img src="/assets/img/goldbook/pca.png" alt="PCA Example">
    <figcaption>Source: [Add Source Here]</figcaption>
  </div>
</div>
