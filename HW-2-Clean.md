HW 2 Clean
================
Jennifer Osei (jao2195)
2022-10-05

``` r
pols_month2 = read_csv("data/pols-month.csv") %>% 
 
  
  janitor::clean_names() %>% 
separate(mon,into = c("month", "day", "year")) 
```

    ## Rows: 822 Columns: 9
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## dbl  (8): prez_gop, gov_gop, sen_gop, rep_gop, prez_dem, gov_dem, sen_dem, r...
    ## date (1): mon
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
View(pols_month2)
# %>% 
#   mutate(year = as.integer(year), month = as.integer(month), day = as.integer(day)) %>% 
#   mutate(month = month.name[month]) %>% 
#   mutate(prez_gop = replace(prez_gop, prez_gop==2, 1 )) %>% 
#   mutate(president = ifelse(prez_gop == '1', 'gop', 'dem')) 
# 
# View(pols_month2)
```
