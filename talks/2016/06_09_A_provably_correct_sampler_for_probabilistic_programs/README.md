# A provably correct sampler for probabilistic programs

[Hur et al.](/a-provably-correct-sampler-for-probabilistic-programs_hur-nori-rajamani-samuel_2015.pdf)
present some of the challenges inherent in implementing samplers for
probabilistic programs and present an algorithm for implementing MCMC inference
and prove its correctness.

## Concrete comparison with Stan

Richard Hydomako has created
[the following iPython notebook](/2016_06_08_infer_paper.ipynb) which
demonstrates how their technique matches up to stan's implementation on the
example presented in Figure 2a in Hur et al. Torsten Scholak has also
contributed [his iPython notebook](/stan_workaround.ipynb) which demonstrates
the source transformation which allows Stan to infer the correct
distribution. This points to a systemic bug in the Stan sampler (see
[stan-dev/stan#1917](https://github.com/stan-dev/stan/issues/1917)).

## Basis of the technique

The technique presented in Hur et al is based on two principles:

- Tracking of samples drawn from random variables along with the distributions
  from whence they were drawn from. This is similar to the bookkeeping we saw
  being done in
  [ProPL #7](/../05_11_Lightweight_implementation_of_ProPL_via_transformational_compilation/README.md)
  in Wingate et al a except that it's a little more involved (and rightly
  so). Specifically, each instance for each variable they track a list of values
  as well as the distributional information with each value. The paper
  demonstrates how, while for simpler cases, techniques such as line-number
  based tracking and/or static single assignment (SSA) forms help, they're
  inadequate in the general case (consider examples where the number of
  iterations are the result of a random sample).

- The second component to their technique is what to do in the case when no
  valid previous value for a given variable is available. For this they utlize
  the
  [Metropolis independent sampling algorithm](/metropolized-independent-sampling-with-comparisons-to-rejection-importance-sampling_liu.pdf).
