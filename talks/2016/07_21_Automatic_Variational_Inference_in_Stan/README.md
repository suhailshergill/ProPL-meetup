# Automatic Variational Inference in Stan

This talk/discussion is centered around
[the more recent version of the paper](http://arxiv.org/abs/1603.00788) on
Automatic Differentiation Variational Inference. The
[original paper from 2015](http://arxiv.org/abs/1506.03431) did not elaborate
quite as much as some of us found the 2016 version (titled "Automatic
Differentiation Variational Inferenve") more accessible.

[Richard Hydomako](https://github.com/rhydomako) has contributed
[an associated ipython notebook](./2016_07_07_notes_on_advi.ipynb) with notes
from the paper touching on the basic ideas.

You can see a better rendering of the above notebook 
[here](http://nbviewer.jupyter.org/github/suhailshergill/ProPL-meetup/blob/propl%239/talks/2016/07_21_Automatic_Variational_Inference_in_Stan/2016_07_07_notes_on_advi.ipynb).

# Notes

- KL-divergence is asymmetric, and Variational Inference (VI) uses one direction. Using the other direction in the "obvious" manner in VI yields a poor approximation. Bishop (2006) has a good discussion on the matter.
- The differentiability of q is needed because of how we're choosing to maximize the ELBO. If we were using a derivative-free optimization procedure we could do away with this.
- The differentiability of T^-1, however, is always required (for the Jacobian).
