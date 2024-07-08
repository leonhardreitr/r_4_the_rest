# Chapter 2


``` r
library(tidyverse)
```

    ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ✔ forcats   1.0.0     ✔ stringr   1.5.1
    ✔ ggplot2   3.5.1     ✔ tibble    3.2.1
    ✔ lubridate 1.9.3     ✔ tidyr     1.3.1
    ✔ purrr     1.0.2     
    ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ✖ dplyr::filter() masks stats::filter()
    ✖ dplyr::lag()    masks stats::lag()
    ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
library(ggthemes)
# Why not just use the excel theme for kicks and giggles
theme_set(
    theme_excel()
)
```

``` r
d <- read_csv("https://data.rfortherestofus.com/gapminder_10_rows.csv")
```

    Rows: 10 Columns: 6
    ── Column specification ────────────────────────────────────────────────────────
    Delimiter: ","
    chr (2): country, continent
    dbl (4): year, lifeExp, pop, gdpPercap

    ℹ Use `spec()` to retrieve the full column specification for this data.
    ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
glimpse(d)
```

    Rows: 10
    Columns: 6
    $ country   <chr> "Afghanistan", "Afghanistan", "Afghanistan", "Afghanistan", …
    $ continent <chr> "Asia", "Asia", "Asia", "Asia", "Asia", "Asia", "Asia", "Asi…
    $ year      <dbl> 1952, 1957, 1962, 1967, 1972, 1977, 1982, 1987, 1992, 1997
    $ lifeExp   <dbl> 28.801, 30.332, 31.997, 34.020, 36.088, 38.438, 39.854, 40.8…
    $ pop       <dbl> 8425333, 9240934, 10267083, 11537966, 13079460, 14880372, 12…
    $ gdpPercap <dbl> 779.4453, 820.8530, 853.1007, 836.1971, 739.9811, 786.1134, …

``` r
#p <- 
d |> 
ggplot(
    aes(
        x = year,
        y = lifeExp
    )
) +
    geom_line(col = "#FF00FF")
```

![](chap2_files/figure-commonmark/unnamed-chunk-2-1.png)
