# A provably correct sampler for probabilistic programs

[Hur et al.](/a-provably-correct-sampler-for-probabilistic-programs_hur-nori-rajamani-samuel_2015.pdf)
present some of the challenges inherent in implementing samplers for
probabilistic programs and present an algorithm for implementing MCMC inference
and prove its correctness.

## Concrete comparison with Stan

Richard Hydomako has created
[the following iPython notebook](https://gist.github.com/rhydomako/bcfc66a3d6947899723eb678b5c5e5c5)
which demonstrates how their technique matches up to stan's implementation on
the example presented in Figure 2a in Hur et al.
