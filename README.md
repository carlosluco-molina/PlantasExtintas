Trabajo plantas extintas
================

# Introducción

En este documento trabajaremos para explorar la identidad de plantas que
se encuentran extintas en silvestria o totalmente extintas según la
[*IUCN*](https://www.iucnredlist.org/)

## Trabajando con los datos

Vamos a partir trabajando con los paquetes necesarios para trabajar.

``` r
library(tidyverse)
```

    ## Warning: package 'tidyverse' was built under R version 4.0.3

    ## -- Attaching packages --------------------------------------- tidyverse 1.3.0 --

    ## v ggplot2 3.3.2     v purrr   0.3.4
    ## v tibble  3.0.4     v dplyr   1.0.2
    ## v tidyr   1.1.2     v stringr 1.4.0
    ## v readr   1.4.0     v forcats 0.5.0

    ## Warning: package 'ggplot2' was built under R version 4.0.3

    ## Warning: package 'tibble' was built under R version 4.0.3

    ## Warning: package 'tidyr' was built under R version 4.0.3

    ## Warning: package 'readr' was built under R version 4.0.3

    ## Warning: package 'purrr' was built under R version 4.0.3

    ## Warning: package 'dplyr' was built under R version 4.0.3

    ## Warning: package 'stringr' was built under R version 4.0.3

    ## Warning: package 'forcats' was built under R version 4.0.3

    ## -- Conflicts ------------------------------------------ tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

ahora voy a leer los datos con los que voy a trabajar:

``` r
plants <- readr::read_csv("https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2020/2020-08-18/plants.csv")
```

    ## 
    ## -- Column specification --------------------------------------------------------
    ## cols(
    ##   .default = col_double(),
    ##   binomial_name = col_character(),
    ##   country = col_character(),
    ##   continent = col_character(),
    ##   group = col_character(),
    ##   year_last_seen = col_character(),
    ##   red_list_category = col_character()
    ## )
    ## i Use `spec()` for the full column specifications.

## Resumen de especies por país

``` r
resumen<-plants %>% dplyr::filter(continent=="South America") %>% group_by(country, binomial_name) %>% summarise(n_species=n())
```

    ## `summarise()` regrouping output by 'country' (override with `.groups` argument)

``` r
resumen
```

    ## # A tibble: 83 x 3
    ## # Groups:   country [9]
    ##    country   binomial_name                       n_species
    ##    <chr>     <chr>                                   <int>
    ##  1 Argentina Senecio leucopeplus                         1
    ##  2 Bolivia   Flabellidium spinosum                       1
    ##  3 Brazil    Brugmansia suaveolens                       1
    ##  4 Brazil    Campomanesia lundiana                       1
    ##  5 Brazil    Cereus estevesii                            1
    ##  6 Brazil    Chrysophyllum januariense                   1
    ##  7 Brazil    Devillea flagelliformis                     1
    ##  8 Brazil    Discocactus subterraneo-proliferans         1
    ##  9 Brazil    Gomidesia cambessedeana                     1
    ## 10 Brazil    Pouteria stenophylla                        1
    ## # ... with 73 more rows
