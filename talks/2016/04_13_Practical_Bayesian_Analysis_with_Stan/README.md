# Practical Bayesian Analysis (with Stan)

This lecture on Bayesian Analysis was held at the [Toronto Probabilistic Programming Meetup](http://www.meetup.com/Toronto-Probabilistic-Programming-Meetup/) at [Architech](http://www.architech.ca/), Toronto, 13 April 2016.


## Dependencies

We will use [R](https://www.r-project.org).
Make sure to install [knitr](http://yihui.name/knitr/) and [pandoc](http://pandoc.org) to compile the document.
The Bayesian part is based on [Stan](http://mc-stan.org) using the [rstan](http://mc-stan.org/interfaces/rstan.html) interface.


Install all dependencies from within R:

```r
install.packages('knitr')    # compile R markdown
install.packages('rstan')    # Stan interface

install.packages('dplyr')    # data munging
install.packages('ggplot2')  # plotting
install.packages('lme4')     # linear mixed models
```


## Compilation

You can compile the R markdown document using `knitr` in R ...

```r
library(knitr)
knit('practicalbayes.Rmd')
```

... followed by these pandoc commands:

```bash
# create PDF
pandoc -s -o practicalbayes.pdf practicalbayes.md 

# create HTML slide show
pandoc -s -i -t slidy --mathml -o practicalbayes.html practicalbayes.md
```


The slide show (.html) might only run correctly using a server.
Start a server in the directory where the .html file resides and open `http://localhost:8000` in a browser

```bash
python -m SimpleHTTPServer
```

