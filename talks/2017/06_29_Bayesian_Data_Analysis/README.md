# Bayesian Data Analysis - a discussion

This was an open-ended discussion and notes weren't taken in this session. The
focus was on some topics from the first four chapters of the book
[Bayesian Data Analysis](https://www.amazon.com/Bayesian-Analysis-Chapman-Statistical-Science/dp/1439840954). More
detail can be found on the
[Meetup page](https://www.meetup.com/Toronto-Probabilistic-Programming-Meetup/events/240283490/).

# Main highlights

## Approximate Bayesian inference via discretization
Some pitfalls:
- This quickly becomes intractable as the dimensionality increases
- Even for small problems, it's not clear how to optimally pick the
  discretization granularity. 

## Variance of the Bayesian posterior
The choice of priors can affect the characteristic of the posterior
distribution, especially if you're using conjugate distributions. In this case
it's prudent to take note of how the variance of the posterior changes as a
result of Bayesian updates.

Some special cases discussed were:
- The Gaussian distribution: In this case the variance always
  decreases. Depending on the problem specifics this may motivate choosing the
  largest possible variance for the prior and/or choosing a non-parametric model
  which allows for a varying number of Gaussian mixtures.

- The Beta-Binomial case: In this case depending on the sequence of
  observations, the variance may actually increase.
