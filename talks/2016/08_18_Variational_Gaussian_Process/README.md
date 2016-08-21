# The Variational Gaussian Process

# Quick Recap
## Bayesian Inference intro
1. Observe the phenomenon
2. Build a model
3. Infer the posterior to **reason** about the phenomenon
4. Iterate / tweak 2
5. Apply the model: eg look at the  [posterior predictive](https://en.wikipedia.org/wiki/Posterior_predictive_distribution) 
(i.e. distribution of prediction/target variable conditional on observed data) if this is a predictive model.

## Variational inference
- Changes step 3. to **approximate** the posterior (and then optimizing the approximation).
- Use ELBO / KL divergence to optimize
  - Using the other direction of KL divergence gives rise to expectation propagation

# Conventional Variational Modeling
- Tradeoff: 
  - make *q* (variational distribution) simpler, or 
  - we make it more expressive (but difficult to optimize): eg something like [Cluster Variational](https://arxiv.org/abs/cond-mat/0508216)
    approach which relaxes the mean-field assumption (in a hierarchical manner)

# Variational Gaussian Process
- Another option: hierarchical variational model. Keep the mean-field assumption, but introduce a prior on it and learn said hyperparameter.
  - Change the parameter space from lambda to theta
  - theta determines functions, *f*, (via a gaussian process) which are evaluated on random variables (both are integrated away) to give lambda
- One possible choice of kernel for Gaussian Process (GP) is the Automatic Relevance Determination kernel


# Parting thoughts
- Connection(s) if any to <https://github.com/suhailshergill/ProPL-meetup/tree/master/talks/2016/07_21_Automatic_Variational_Inference_in_Stan>
- Universality of Gaussian Processes in VGP context: Universal approximation function
  - How much of this is a consequence of things such as [Mercer's theorem](https://en.wikipedia.org/wiki/Mercer%27s_theorem)?
- What's the impact of replacing the gaussian distribution with something else?
  - You may lose one of the properties that the second-order statistic defines properties.
- Size of the "variational dataset"
- What is the motivation to connect it to autoencoders?


# Resources
- [Printable version](talk.pdf) of the slides
- [Video recording](http://videolectures.net/iclr2016_tran_variational_gaussian/) of a talk given by Dustin Tran on his paper
- [IPython Notebook](gaussian_processes.ipynb) demonstrating Gaussian process regression
- The presentation's [repository](https://github.com/tscholak/variational_gaussian_process)
- [Preprints](http://arxiv.org/find/stat/1/au:+Blei_D/0/1/0/all/0/1) of Blei Lab articles
