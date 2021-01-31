HW 3, pt. 1: Tidying `dadmom`
================
Julia Du

# Get the data

``` r
# don't modify this chunk unless you still need to install rcfss
# if so, run "devtools::install_github("uc-cfss/rcfss")" in the console first

library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.0 ──

    ## ✓ ggplot2 3.3.3     ✓ purrr   0.3.4
    ## ✓ tibble  3.0.4     ✓ dplyr   1.0.2
    ## ✓ tidyr   1.1.2     ✓ stringr 1.4.0
    ## ✓ readr   1.4.0     ✓ forcats 0.5.0

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
library(rcfss)

data("dadmom")
dadmom
```

    ## # A tibble: 3 x 5
    ##   famid named  incd namem  incm
    ##   <dbl> <chr> <dbl> <chr> <dbl>
    ## 1     1 Bill  30000 Bess  15000
    ## 2     2 Art   22000 Amy   18000
    ## 3     3 Paul  25000 Pat   50000

# Tidied data

``` r
# write your code to tidy the data 

library(tidyverse)
library(rcfss)

dadmom %>%
pivot_longer(cols = -famid, names_to = "parent", values_to = "values", values_transform = list(values = as.character)) %>%
  separate(parent, into = c("name", "gender"), sep = -1) %>%
  pivot_wider(names_from = name, values_from = values)
```

    ## # A tibble: 6 x 4
    ##   famid gender name  inc  
    ##   <dbl> <chr>  <chr> <chr>
    ## 1     1 d      Bill  30000
    ## 2     1 m      Bess  15000
    ## 3     2 d      Art   22000
    ## 4     2 m      Amy   18000
    ## 5     3 d      Paul  25000
    ## 6     3 m      Pat   50000

``` r
#TA's fancy method
dadmom %>%
  pivot_longer(cols = -famid, names_to = c(".value", "type"), names_sep = -1)
```

    ## # A tibble: 6 x 4
    ##   famid type  name    inc
    ##   <dbl> <chr> <chr> <dbl>
    ## 1     1 d     Bill  30000
    ## 2     1 m     Bess  15000
    ## 3     2 d     Art   22000
    ## 4     2 m     Amy   18000
    ## 5     3 d     Paul  25000
    ## 6     3 m     Pat   50000

## Session info

``` r
# don't modify this chunk
devtools::session_info()
```

    ## ─ Session info ───────────────────────────────────────────────────────────────
    ##  setting  value                               
    ##  version  R version 4.0.1 (2020-06-06)        
    ##  os       Red Hat Enterprise Linux 8.3 (Ootpa)
    ##  system   x86_64, linux-gnu                   
    ##  ui       X11                                 
    ##  language (EN)                                
    ##  collate  en_US.UTF-8                         
    ##  ctype    en_US.UTF-8                         
    ##  tz       America/Chicago                     
    ##  date     2021-01-30                          
    ## 
    ## ─ Packages ───────────────────────────────────────────────────────────────────
    ##  package     * version date       lib source                        
    ##  assertthat    0.2.1   2019-03-21 [2] CRAN (R 4.0.1)                
    ##  backports     1.2.1   2020-12-09 [2] CRAN (R 4.0.1)                
    ##  broom         0.7.3   2020-12-16 [2] CRAN (R 4.0.1)                
    ##  callr         3.5.1   2020-10-13 [2] CRAN (R 4.0.1)                
    ##  cellranger    1.1.0   2016-07-27 [2] CRAN (R 4.0.1)                
    ##  cli           2.2.0   2020-11-20 [2] CRAN (R 4.0.1)                
    ##  colorspace    2.0-0   2020-11-11 [2] CRAN (R 4.0.1)                
    ##  crayon        1.3.4   2017-09-16 [2] CRAN (R 4.0.1)                
    ##  DBI           1.1.0   2019-12-15 [2] CRAN (R 4.0.1)                
    ##  dbplyr        2.0.0   2020-11-03 [2] CRAN (R 4.0.1)                
    ##  desc          1.2.0   2018-05-01 [2] CRAN (R 4.0.1)                
    ##  devtools      2.3.2   2020-09-18 [1] CRAN (R 4.0.1)                
    ##  digest        0.6.27  2020-10-24 [2] CRAN (R 4.0.1)                
    ##  dplyr       * 1.0.2   2020-08-18 [2] CRAN (R 4.0.1)                
    ##  ellipsis      0.3.1   2020-05-15 [2] CRAN (R 4.0.1)                
    ##  evaluate      0.14    2019-05-28 [2] CRAN (R 4.0.1)                
    ##  fansi         0.4.1   2020-01-08 [2] CRAN (R 4.0.1)                
    ##  forcats     * 0.5.0   2020-03-01 [2] CRAN (R 4.0.1)                
    ##  fs            1.5.0   2020-07-31 [2] CRAN (R 4.0.1)                
    ##  generics      0.1.0   2020-10-31 [2] CRAN (R 4.0.1)                
    ##  ggplot2     * 3.3.3   2020-12-30 [2] CRAN (R 4.0.1)                
    ##  glue          1.4.2   2020-08-27 [2] CRAN (R 4.0.1)                
    ##  gtable        0.3.0   2019-03-25 [2] CRAN (R 4.0.1)                
    ##  haven         2.3.1   2020-06-01 [2] CRAN (R 4.0.1)                
    ##  hms           0.5.3   2020-01-08 [2] CRAN (R 4.0.1)                
    ##  htmltools     0.4.0   2019-10-04 [2] CRAN (R 4.0.1)                
    ##  httr          1.4.2   2020-07-20 [2] CRAN (R 4.0.1)                
    ##  jsonlite      1.7.2   2020-12-09 [2] CRAN (R 4.0.1)                
    ##  knitr         1.30    2020-09-22 [2] CRAN (R 4.0.1)                
    ##  lifecycle     0.2.0   2020-03-06 [2] CRAN (R 4.0.1)                
    ##  lubridate     1.7.9.2 2020-11-13 [2] CRAN (R 4.0.1)                
    ##  magrittr      2.0.1   2020-11-17 [2] CRAN (R 4.0.1)                
    ##  memoise       1.1.0   2017-04-21 [2] CRAN (R 4.0.1)                
    ##  modelr        0.1.8   2020-05-19 [2] CRAN (R 4.0.1)                
    ##  munsell       0.5.0   2018-06-12 [2] CRAN (R 4.0.1)                
    ##  pillar        1.4.7   2020-11-20 [2] CRAN (R 4.0.1)                
    ##  pkgbuild      1.2.0   2020-12-15 [2] CRAN (R 4.0.1)                
    ##  pkgconfig     2.0.3   2019-09-22 [2] CRAN (R 4.0.1)                
    ##  pkgload       1.1.0   2020-05-29 [2] CRAN (R 4.0.1)                
    ##  prettyunits   1.1.1   2020-01-24 [2] CRAN (R 4.0.1)                
    ##  processx      3.4.5   2020-11-30 [2] CRAN (R 4.0.1)                
    ##  ps            1.5.0   2020-12-05 [2] CRAN (R 4.0.1)                
    ##  purrr       * 0.3.4   2020-04-17 [2] CRAN (R 4.0.1)                
    ##  R6            2.5.0   2020-10-28 [2] CRAN (R 4.0.1)                
    ##  rcfss       * 0.2.1   2021-01-05 [2] Github (uc-cfss/rcfss@36e77a2)
    ##  Rcpp          1.0.5   2020-07-06 [2] CRAN (R 4.0.1)                
    ##  readr       * 1.4.0   2020-10-05 [2] CRAN (R 4.0.1)                
    ##  readxl        1.3.1   2019-03-13 [2] CRAN (R 4.0.1)                
    ##  remotes       2.2.0   2020-07-21 [2] CRAN (R 4.0.1)                
    ##  reprex        0.3.0   2019-05-16 [1] CRAN (R 4.0.1)                
    ##  rlang         0.4.10  2020-12-30 [2] CRAN (R 4.0.1)                
    ##  rmarkdown     2.6     2020-12-14 [2] CRAN (R 4.0.1)                
    ##  rprojroot     2.0.2   2020-11-15 [2] CRAN (R 4.0.1)                
    ##  rstudioapi    0.13    2020-11-12 [2] CRAN (R 4.0.1)                
    ##  rvest         0.3.6   2020-07-25 [2] CRAN (R 4.0.1)                
    ##  scales        1.1.1   2020-05-11 [2] CRAN (R 4.0.1)                
    ##  sessioninfo   1.1.1   2018-11-05 [2] CRAN (R 4.0.1)                
    ##  stringi       1.5.3   2020-09-09 [2] CRAN (R 4.0.1)                
    ##  stringr     * 1.4.0   2019-02-10 [2] CRAN (R 4.0.1)                
    ##  testthat      3.0.1   2020-12-17 [2] CRAN (R 4.0.1)                
    ##  tibble      * 3.0.4   2020-10-12 [2] CRAN (R 4.0.1)                
    ##  tidyr       * 1.1.2   2020-08-27 [2] CRAN (R 4.0.1)                
    ##  tidyselect    1.1.0   2020-05-11 [2] CRAN (R 4.0.1)                
    ##  tidyverse   * 1.3.0   2019-11-21 [1] CRAN (R 4.0.1)                
    ##  usethis       2.0.0   2020-12-10 [1] CRAN (R 4.0.1)                
    ##  utf8          1.1.4   2018-05-24 [2] CRAN (R 4.0.1)                
    ##  vctrs         0.3.6   2020-12-17 [2] CRAN (R 4.0.1)                
    ##  withr         2.3.0   2020-09-22 [2] CRAN (R 4.0.1)                
    ##  xfun          0.19    2020-10-30 [2] CRAN (R 4.0.1)                
    ##  xml2          1.3.2   2020-04-23 [2] CRAN (R 4.0.1)                
    ##  yaml          2.2.1   2020-02-01 [2] CRAN (R 4.0.1)                
    ## 
    ## [1] /home/duj/R/x86_64-pc-linux-gnu-library/4.0
    ## [2] /opt/R/4.0.1/lib/R/library
