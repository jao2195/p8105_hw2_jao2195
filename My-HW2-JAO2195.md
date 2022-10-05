Data Science - Homework 2
================
Jennifer Osei (jao2195)
October 4, 2022

\#Problem 2 This problem uses the Mr. Trash Wheel dataset, available as
an Excel file on the course website.

Read and clean the Mr. Trash Wheel sheet:

specify the sheet in the Excel file and to omit non-data entries (rows
with notes / figures; columns containing notes) using arguments in
read_excel use reasonable variable names omit rows that do not include
dumpster-specific data round the number of sports balls to the nearest
integer and converts the result to an integer variable (using
as.integer) Use a similar process to import, clean, and organize the
data for Professor Trash Wheel, and combine this with the Mr. Trash
Wheel dataset to produce a single tidy dataset. To keep track of which
Trash Wheel is which, you may need to add an additional variable to both
datasets before combining.

Write a paragraph about these data; you are encouraged to use inline R.
Be sure to note the number of observations in the resulting dataset, and
give examples of key variables. For available data, what was the total
weight of trash collected by Professor Trash Wheel? What was the total
number of sports balls collected by Mr. Trash Wheel in 2020?

``` r
library(tidyverse)
library(readxl)
library(readr)
```

``` r
trash_wheel = read_excel("data/trashwheel.xlsx", sheet = "Mr. Trash Wheel")
```

    ## New names:
    ## • `` -> `...15`
    ## • `` -> `...16`

``` r
View(trash_wheel) 
```

\#Problem 3 This problem uses the FiveThirtyEight data; these data were
gathered to create the interactive graphic on this page. In particular,
we’ll use the data in pols-month.csv, unemployment.csv, and snp.csv. Our
goal is to merge these into a single data frame using year and month as
keys across datasets.

``` r
pols_month <- read_csv("data/pols-month.csv")
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
View(pols_month)

snp <- read_csv("data/snp.csv")
```

    ## Rows: 787 Columns: 2
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (1): date
    ## dbl (1): close
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
View(snp)

unemployment <- read_csv("data/unemployment.csv")
```

    ## Rows: 68 Columns: 13
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## dbl (13): Year, Jan, Feb, Mar, Apr, May, Jun, Jul, Aug, Sep, Oct, Nov, Dec
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
View(unemployment)
```

First, clean the data in pols-month.csv. Use separate() to break up the
variable mon into integer variables year, month, and day; replace month
number with month name; create a president variable taking values gop
and dem, and remove prez_dem and prez_gop; and remove the day variable.

Second, clean the data in snp.csv using a similar process to the above.
For consistency across datasets, arrange according to year and month,
and organize so that year and month are the leading columns.

Third, tidy the unemployment data so that it can be merged with the
previous datasets. This process will involve switching from “wide” to
“long” format; ensuring that key variables have the same name; and
ensuring that key variables take the same values.

Join the datasets by merging snp into pols, and merging unemployment
into the result.

Write a short paragraph about these datasets. Explain briefly what each
dataset contained, and describe the resulting dataset (e.g. give the
dimension, range of years, and names of key variables).

Note: we could have used a date variable as a key instead of creating
year and month keys; doing so would help with some kinds of plotting,
and be a more accurate representation of the data. Date formats are
tricky, though. For more information check out the lubridate package in
the tidyverse
