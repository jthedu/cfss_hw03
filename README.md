# Homework 03: Exploring and wrangling data

Here is my [dadmom source code](dadmom.Rmd) & my [dadmom rendered report](dadmom.md).
Here also is my [scotus source code](scotus.Rmd) & my [scotus rendered report](scotus.md).

And here is how I felt [showing my work to my family](https://www.youtube.com/watch?v=LCUze7kuNas).

Detailed instructions for this homework assignment are [here](https://cfss.uchicago.edu/homework/explore-data/).

## Required packages

You should have the following packages installed:

```r
library(tidyverse)
library(gapminder)
library(rcfss)

library(readr)
library(lubridate)
library(ggthemes)
library('scales')
library(forcats)

```

[`rcfss`](https://github.com/uc-cfss/rcfss) can be installed from GitHub using the command:

```r
if (packageVersion("devtools") < 1.6) {
  install.packages("devtools")
}

devtools::install_github("uc-cfss/rcfss")
```

## Assignment submission

Your assignment should be submitted as three RMarkdown documents. Make sure you've read the chapter on [R Markdown](http://r4ds.had.co.nz/r-markdown.html) so you understand how to properly use these files.

For your benefit, I have provided starter RMarkdown documents for each part of the homework. You should not need to modify the starter code, merely add on to it. In the [`demo`](demo/) folder I have included some example solutions:

* [Tidying `dadmom` solution](demo/dadmom_solution.md)
* [SCOTUS solution](demo/scotus_solution.md)
