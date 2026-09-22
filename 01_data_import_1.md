Data Import
================
Ali Early

This file is for doing data import.

``` r
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.2.1     ✔ readr     2.2.0
    ## ✔ forcats   1.0.1     ✔ stringr   1.6.0
    ## ✔ ggplot2   4.0.3     ✔ tibble    3.3.1
    ## ✔ lubridate 1.9.5     ✔ tidyr     1.3.2
    ## ✔ purrr     1.2.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
litters_df =
  read_csv(file = "data/FAS_litters.csv")
```

    ## Rows: 49 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (4): Group, Litter Number, GD0 weight, GD18 weight
    ## dbl (4): GD of Birth, Pups born alive, Pups dead @ birth, Pups survive
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
litters_df = janitor::clean_names(litters_df)
```

``` r
pups_df =
  read_csv(file = "data/FAS_pups.csv", skip = 3)
```

    ## Rows: 313 Columns: 6
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): Litter Number, PD ears
    ## dbl (4): Sex, PD eyes, PD pivot, PD walk
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
litters_df = janitor::clean_names(pups_df)
```

## Look at the data

``` r
litters_df
```

    ## # A tibble: 313 × 6
    ##    litter_number   sex pd_ears pd_eyes pd_pivot pd_walk
    ##    <chr>         <dbl> <chr>     <dbl>    <dbl>   <dbl>
    ##  1 #85               1 4            13        7      11
    ##  2 #85               1 4            13        7      12
    ##  3 #1/2/95/2         1 5            13        7       9
    ##  4 #1/2/95/2         1 5            13        8      10
    ##  5 #5/5/3/83/3-3     1 5            13        8      10
    ##  6 #5/5/3/83/3-3     1 5            14        6       9
    ##  7 #5/4/2/95/2       1 .            14        5       9
    ##  8 #4/2/95/3-3       1 4            13        6       8
    ##  9 #4/2/95/3-3       1 4            13        7       9
    ## 10 #2/2/95/3-2       1 4            NA        8      10
    ## # ℹ 303 more rows

``` r
pups_df
```

    ## # A tibble: 313 × 6
    ##    `Litter Number`   Sex `PD ears` `PD eyes` `PD pivot` `PD walk`
    ##    <chr>           <dbl> <chr>         <dbl>      <dbl>     <dbl>
    ##  1 #85                 1 4                13          7        11
    ##  2 #85                 1 4                13          7        12
    ##  3 #1/2/95/2           1 5                13          7         9
    ##  4 #1/2/95/2           1 5                13          8        10
    ##  5 #5/5/3/83/3-3       1 5                13          8        10
    ##  6 #5/5/3/83/3-3       1 5                14          6         9
    ##  7 #5/4/2/95/2         1 .                14          5         9
    ##  8 #4/2/95/3-3         1 4                13          6         8
    ##  9 #4/2/95/3-3         1 4                13          7         9
    ## 10 #2/2/95/3-2         1 4                NA          8        10
    ## # ℹ 303 more rows
