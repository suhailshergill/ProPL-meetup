# Lightweight implementation of ProPL via transformational compilation

[Wingate et al. a](/lightweight-implementations-of-ProPL-via-transformational-compilation_wingate-stuhlmuller-goodman_2011.pdf)
presented a general method of turning any programming language into a
probabilistic programming system with an MCMC inference scheme. The key ideas of
the paper were as follows

## Wingate technique

### Naming each random choice in the probabilistic program

The premise is of a closed set of Exchangeable Random Primitives (ERP). Each ERP
then is then provided a key and can be replaced with a lookup in a global
database (similar to where, say, memoized values of ERP invocations are being
stored), given that reference name as key. In this manner you transform a
stochastic program into a deterministic program, given a fixed global database.

The paper went into length about the specifics of the naming scheme to use
(trying to maximize sharing by providing ERPs the same reference).

### Bookkeeping in the global database

The global database records a few details (this enables MCMC inference):

- The assigned ERP name/ID. This is the lookup key.
- The value sampled last time the ERP was invoked.
- The type of ERP (e.g., `uniform`, `dirac` etc).
- The parameters being passed to the ERP.
- The log-likelihood of the sample.

### Carrying out MCMC by updating entries in global database

The paper defines an MCMC algorithm which works by updating entries in the
global database. Note that given a version of the database, the transformed
program is deterministic. The MCMC inference proceeds in the trace
space. Updating the database from `D` to `D'` corresponds to a proposal and the
paper defines the Metropolis-Hastings (MH) acceptance criteria.

## Limitations of Wingate technique

The limitations of the technique are highlighted in
[Kiselyov](/problems-of-the-lightweight-implementation-of-probabilistic-programming_kiselyov_2016.pdf). To
summarize:

### Limitations of MCMC

MCMC is a general purpose inference scheme, however, it is not without its
limitations. More advanced techniques like Hamiltonion Monte Carlo (HMC) and
Riemannian Manifold HMC (RMHMC) solve some of these problems. A followup paper
[Wingate et al. b](https://stuhlmueller.org/papers/nonstandard-interpretations-nips2011.pdf)
looked at using HMC.

### The technique as presented in the paper does not handle code refactoring

Minor changes in the code, while not changing the semantics of the stochastic
program can have an impact on the result of the inference. Part of the reason is
that the naming scheme advocated for in the paper tries to reuse names too
much. A better approach is to give unique names, and then use some static
analysis to identify the dependencies, so that when one entry in the database is
resampled the ones dependent on it are resampled as well (this reduces
likelihood of rejection at the MH step).

### The technique doesn't handle conditioning nested within conditional branches

The paper doesn't give an algorithm for tackling this case and when the
"straightforward" approach is tried it's found to not converge to the correct
results per
[Kiselyov](/problems-of-the-lightweight-implementation-of-probabilistic-programming_kiselyov_2016.pdf). That
paper points to an implementation where they seemingly have overcome this
hurdle, but without a formal proof of correctness of the inference scheme. This
is clearly an active area of research.
