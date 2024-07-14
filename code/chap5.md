# Chapter 5


Time to make some tables

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
library(gapminder)
library(gt)
library(gtExtras)
```

``` r
d <- gapminder %>%
  filter(country %in% c("Afghanistan", "Albania", "Algeria", "Angola")) %>%
  select(country, year, gdpPercap) %>%
  mutate(country = as.character(country)) %>%
  pivot_wider(
    id_cols = country,
    names_from = year,
    values_from = gdpPercap
  ) %>%
  select(country, `1952`, `1972`, `1992`) %>%
  rename(Country = country)
```

Rule 1: Less grid lines

``` r
t <- 
d |> 
    gt() |> 
    tab_style(
        style = cell_borders(color = "transparent"),
        locations = cells_body()
    )
t
```

<div id="cvrdpurazp" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#cvrdpurazp table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
&#10;#cvrdpurazp thead, #cvrdpurazp tbody, #cvrdpurazp tfoot, #cvrdpurazp tr, #cvrdpurazp td, #cvrdpurazp th {
  border-style: none;
}
&#10;#cvrdpurazp p {
  margin: 0;
  padding: 0;
}
&#10;#cvrdpurazp .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}
&#10;#cvrdpurazp .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}
&#10;#cvrdpurazp .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}
&#10;#cvrdpurazp .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}
&#10;#cvrdpurazp .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#cvrdpurazp .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#cvrdpurazp .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#cvrdpurazp .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}
&#10;#cvrdpurazp .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}
&#10;#cvrdpurazp .gt_column_spanner_outer:first-child {
  padding-left: 0;
}
&#10;#cvrdpurazp .gt_column_spanner_outer:last-child {
  padding-right: 0;
}
&#10;#cvrdpurazp .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}
&#10;#cvrdpurazp .gt_spanner_row {
  border-bottom-style: hidden;
}
&#10;#cvrdpurazp .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}
&#10;#cvrdpurazp .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}
&#10;#cvrdpurazp .gt_from_md > :first-child {
  margin-top: 0;
}
&#10;#cvrdpurazp .gt_from_md > :last-child {
  margin-bottom: 0;
}
&#10;#cvrdpurazp .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}
&#10;#cvrdpurazp .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#cvrdpurazp .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}
&#10;#cvrdpurazp .gt_row_group_first td {
  border-top-width: 2px;
}
&#10;#cvrdpurazp .gt_row_group_first th {
  border-top-width: 2px;
}
&#10;#cvrdpurazp .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#cvrdpurazp .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}
&#10;#cvrdpurazp .gt_first_summary_row.thick {
  border-top-width: 2px;
}
&#10;#cvrdpurazp .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#cvrdpurazp .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#cvrdpurazp .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}
&#10;#cvrdpurazp .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}
&#10;#cvrdpurazp .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}
&#10;#cvrdpurazp .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#cvrdpurazp .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#cvrdpurazp .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#cvrdpurazp .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#cvrdpurazp .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#cvrdpurazp .gt_left {
  text-align: left;
}
&#10;#cvrdpurazp .gt_center {
  text-align: center;
}
&#10;#cvrdpurazp .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}
&#10;#cvrdpurazp .gt_font_normal {
  font-weight: normal;
}
&#10;#cvrdpurazp .gt_font_bold {
  font-weight: bold;
}
&#10;#cvrdpurazp .gt_font_italic {
  font-style: italic;
}
&#10;#cvrdpurazp .gt_super {
  font-size: 65%;
}
&#10;#cvrdpurazp .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}
&#10;#cvrdpurazp .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}
&#10;#cvrdpurazp .gt_indent_1 {
  text-indent: 5px;
}
&#10;#cvrdpurazp .gt_indent_2 {
  text-indent: 10px;
}
&#10;#cvrdpurazp .gt_indent_3 {
  text-indent: 15px;
}
&#10;#cvrdpurazp .gt_indent_4 {
  text-indent: 20px;
}
&#10;#cvrdpurazp .gt_indent_5 {
  text-indent: 25px;
}
</style>

| Country     | 1952      | 1972      | 1992      |
|-------------|-----------|-----------|-----------|
| Afghanistan | 779.4453  | 739.9811  | 649.3414  |
| Albania     | 1601.0561 | 3313.4222 | 2497.4379 |
| Algeria     | 2449.0082 | 4182.6638 | 5023.2166 |
| Angola      | 3520.6103 | 5473.2880 | 2627.8457 |

</div>

Rule 2: Differentiate the Header from the Body

``` r
t <- 
t |> 
tab_style(
    style = cell_text(weight = "bold"),
    locations = cells_column_labels()
)

t
```

<div id="ptfuuxwqcp" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#ptfuuxwqcp table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
&#10;#ptfuuxwqcp thead, #ptfuuxwqcp tbody, #ptfuuxwqcp tfoot, #ptfuuxwqcp tr, #ptfuuxwqcp td, #ptfuuxwqcp th {
  border-style: none;
}
&#10;#ptfuuxwqcp p {
  margin: 0;
  padding: 0;
}
&#10;#ptfuuxwqcp .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}
&#10;#ptfuuxwqcp .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}
&#10;#ptfuuxwqcp .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}
&#10;#ptfuuxwqcp .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}
&#10;#ptfuuxwqcp .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#ptfuuxwqcp .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#ptfuuxwqcp .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#ptfuuxwqcp .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}
&#10;#ptfuuxwqcp .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}
&#10;#ptfuuxwqcp .gt_column_spanner_outer:first-child {
  padding-left: 0;
}
&#10;#ptfuuxwqcp .gt_column_spanner_outer:last-child {
  padding-right: 0;
}
&#10;#ptfuuxwqcp .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}
&#10;#ptfuuxwqcp .gt_spanner_row {
  border-bottom-style: hidden;
}
&#10;#ptfuuxwqcp .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}
&#10;#ptfuuxwqcp .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}
&#10;#ptfuuxwqcp .gt_from_md > :first-child {
  margin-top: 0;
}
&#10;#ptfuuxwqcp .gt_from_md > :last-child {
  margin-bottom: 0;
}
&#10;#ptfuuxwqcp .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}
&#10;#ptfuuxwqcp .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#ptfuuxwqcp .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}
&#10;#ptfuuxwqcp .gt_row_group_first td {
  border-top-width: 2px;
}
&#10;#ptfuuxwqcp .gt_row_group_first th {
  border-top-width: 2px;
}
&#10;#ptfuuxwqcp .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#ptfuuxwqcp .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}
&#10;#ptfuuxwqcp .gt_first_summary_row.thick {
  border-top-width: 2px;
}
&#10;#ptfuuxwqcp .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#ptfuuxwqcp .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#ptfuuxwqcp .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}
&#10;#ptfuuxwqcp .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}
&#10;#ptfuuxwqcp .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}
&#10;#ptfuuxwqcp .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#ptfuuxwqcp .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#ptfuuxwqcp .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#ptfuuxwqcp .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#ptfuuxwqcp .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#ptfuuxwqcp .gt_left {
  text-align: left;
}
&#10;#ptfuuxwqcp .gt_center {
  text-align: center;
}
&#10;#ptfuuxwqcp .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}
&#10;#ptfuuxwqcp .gt_font_normal {
  font-weight: normal;
}
&#10;#ptfuuxwqcp .gt_font_bold {
  font-weight: bold;
}
&#10;#ptfuuxwqcp .gt_font_italic {
  font-style: italic;
}
&#10;#ptfuuxwqcp .gt_super {
  font-size: 65%;
}
&#10;#ptfuuxwqcp .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}
&#10;#ptfuuxwqcp .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}
&#10;#ptfuuxwqcp .gt_indent_1 {
  text-indent: 5px;
}
&#10;#ptfuuxwqcp .gt_indent_2 {
  text-indent: 10px;
}
&#10;#ptfuuxwqcp .gt_indent_3 {
  text-indent: 15px;
}
&#10;#ptfuuxwqcp .gt_indent_4 {
  text-indent: 20px;
}
&#10;#ptfuuxwqcp .gt_indent_5 {
  text-indent: 25px;
}
</style>

| Country     | 1952      | 1972      | 1992      |
|-------------|-----------|-----------|-----------|
| Afghanistan | 779.4453  | 739.9811  | 649.3414  |
| Albania     | 1601.0561 | 3313.4222 | 2497.4379 |
| Algeria     | 2449.0082 | 4182.6638 | 5023.2166 |
| Angola      | 3520.6103 | 5473.2880 | 2627.8457 |

</div>

Rule 3: Align properly

``` r
cat("gt already does that correctly, that is right-align numbers and left-align characters")
```

    gt already does that correctly, that is right-align numbers and left-align characters

Rule 4: Use the Correct Level of Precision Especialy when it comes to
decimals of numbers. Remove them if they are not important

``` {-r}
t <- 
    t |> 
    fmt_currency(
        columns = -"Country",
        decimals = 0, 
        use_seps = F
    )

t
```

Rule 5: Use Color Intentionally

``` {-r}
# is this code in the book wrong?
t <- 
    t |> 
    tab_style(
    style = cell_text(
      color = "orange",
      weight = "bold"
    ),
    locations = cells_body(
      columns = `1952`,
      rows = `1952` == max(`1952`)
    )
  )
    )
t
```

Rule 6: Add a Data Visualization Where Appropriate

``` r
gdp_with_trend <- d %>%
  group_by(Country) %>%
  mutate(Trend = list(c(`1952`, `1972`, `1992`))) %>%
  ungroup()

gdp_with_trend %>%
  gt() %>%
  tab_style(
    style = cell_borders(color = "transparent"),
    locations = cells_body()
  ) %>%
  tab_style(
    style = cell_text(weight = "bold"),
    locations = cells_column_labels()
  ) %>%
  fmt_currency(
    columns = c(`1952`, `1972`, `1992`),
    decimals = 0
  ) %>%
  tab_style(
    style = cell_text(
      color = "orange",
      weight = "bold"
    ),
    locations = cells_body(
      columns = `1952`,
      rows = `1952` == max(`1952`)
    )
  ) %>%
  tab_style(
    style = cell_text(
      color = "orange",
      weight = "bold"
    ),
    locations = cells_body(
      columns = `1972`,
      rows = `1972` == max(`1972`)
    )
  ) %>%
  tab_style(
    style = cell_text(
      color = "orange",
      weight = "bold"
    ),
    locations = cells_body(
      columns = `1992`,
      rows = `1992` == max(`1992`)
    )
  ) %>%
  gt_plt_sparkline(
    column = Trend,
    label = FALSE,
    palette = c("black", "transparent", "transparent", "transparent", "transparent")
  )
```

<div id="lkmdhpnmmy" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#lkmdhpnmmy table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
&#10;#lkmdhpnmmy thead, #lkmdhpnmmy tbody, #lkmdhpnmmy tfoot, #lkmdhpnmmy tr, #lkmdhpnmmy td, #lkmdhpnmmy th {
  border-style: none;
}
&#10;#lkmdhpnmmy p {
  margin: 0;
  padding: 0;
}
&#10;#lkmdhpnmmy .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}
&#10;#lkmdhpnmmy .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}
&#10;#lkmdhpnmmy .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}
&#10;#lkmdhpnmmy .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}
&#10;#lkmdhpnmmy .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#lkmdhpnmmy .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#lkmdhpnmmy .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}
&#10;#lkmdhpnmmy .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}
&#10;#lkmdhpnmmy .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}
&#10;#lkmdhpnmmy .gt_column_spanner_outer:first-child {
  padding-left: 0;
}
&#10;#lkmdhpnmmy .gt_column_spanner_outer:last-child {
  padding-right: 0;
}
&#10;#lkmdhpnmmy .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}
&#10;#lkmdhpnmmy .gt_spanner_row {
  border-bottom-style: hidden;
}
&#10;#lkmdhpnmmy .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}
&#10;#lkmdhpnmmy .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}
&#10;#lkmdhpnmmy .gt_from_md > :first-child {
  margin-top: 0;
}
&#10;#lkmdhpnmmy .gt_from_md > :last-child {
  margin-bottom: 0;
}
&#10;#lkmdhpnmmy .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}
&#10;#lkmdhpnmmy .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#lkmdhpnmmy .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}
&#10;#lkmdhpnmmy .gt_row_group_first td {
  border-top-width: 2px;
}
&#10;#lkmdhpnmmy .gt_row_group_first th {
  border-top-width: 2px;
}
&#10;#lkmdhpnmmy .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#lkmdhpnmmy .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}
&#10;#lkmdhpnmmy .gt_first_summary_row.thick {
  border-top-width: 2px;
}
&#10;#lkmdhpnmmy .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#lkmdhpnmmy .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#lkmdhpnmmy .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}
&#10;#lkmdhpnmmy .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}
&#10;#lkmdhpnmmy .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}
&#10;#lkmdhpnmmy .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}
&#10;#lkmdhpnmmy .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#lkmdhpnmmy .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#lkmdhpnmmy .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}
&#10;#lkmdhpnmmy .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}
&#10;#lkmdhpnmmy .gt_left {
  text-align: left;
}
&#10;#lkmdhpnmmy .gt_center {
  text-align: center;
}
&#10;#lkmdhpnmmy .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}
&#10;#lkmdhpnmmy .gt_font_normal {
  font-weight: normal;
}
&#10;#lkmdhpnmmy .gt_font_bold {
  font-weight: bold;
}
&#10;#lkmdhpnmmy .gt_font_italic {
  font-style: italic;
}
&#10;#lkmdhpnmmy .gt_super {
  font-size: 65%;
}
&#10;#lkmdhpnmmy .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}
&#10;#lkmdhpnmmy .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}
&#10;#lkmdhpnmmy .gt_indent_1 {
  text-indent: 5px;
}
&#10;#lkmdhpnmmy .gt_indent_2 {
  text-indent: 10px;
}
&#10;#lkmdhpnmmy .gt_indent_3 {
  text-indent: 15px;
}
&#10;#lkmdhpnmmy .gt_indent_4 {
  text-indent: 20px;
}
&#10;#lkmdhpnmmy .gt_indent_5 {
  text-indent: 25px;
}
</style>

<table class="gt_table" data-quarto-postprocess="true"
data-quarto-disable-processing="false" data-quarto-bootstrap="false">
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header gt_col_headings">
<th id="Country" class="gt_col_heading gt_columns_bottom_border gt_left"
data-quarto-table-cell-role="th" style="font-weight: bold"
scope="col">Country</th>
<th id="1952" class="gt_col_heading gt_columns_bottom_border gt_right"
data-quarto-table-cell-role="th" style="font-weight: bold"
scope="col">1952</th>
<th id="1972" class="gt_col_heading gt_columns_bottom_border gt_right"
data-quarto-table-cell-role="th" style="font-weight: bold"
scope="col">1972</th>
<th id="1992" class="gt_col_heading gt_columns_bottom_border gt_right"
data-quarto-table-cell-role="th" style="font-weight: bold"
scope="col">1992</th>
<th id="Trend" class="gt_col_heading gt_columns_bottom_border gt_center"
data-quarto-table-cell-role="th" style="font-weight: bold"
scope="col">Trend</th>
</tr>
</thead>
<tbody class="gt_table_body">
<tr class="odd">
<td class="gt_row gt_left" headers="Country"
style="border-left-width: 1px; border-left-style: solid; border-left-color: transparent; border-right-width: 1px; border-right-style: solid; border-right-color: transparent; border-top-width: 1px; border-top-style: solid; border-top-color: transparent; border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: transparent">Afghanistan</td>
<td class="gt_row gt_right" headers="1952"
style="border-left-width: 1px; border-left-style: solid; border-left-color: transparent; border-right-width: 1px; border-right-style: solid; border-right-color: transparent; border-top-width: 1px; border-top-style: solid; border-top-color: transparent; border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: transparent">$779</td>
<td class="gt_row gt_right" headers="1972"
style="border-left-width: 1px; border-left-style: solid; border-left-color: transparent; border-right-width: 1px; border-right-style: solid; border-right-color: transparent; border-top-width: 1px; border-top-style: solid; border-top-color: transparent; border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: transparent">$740</td>
<td class="gt_row gt_right" headers="1992"
style="border-left-width: 1px; border-left-style: solid; border-left-color: transparent; border-right-width: 1px; border-right-style: solid; border-right-color: transparent; border-top-width: 1px; border-top-style: solid; border-top-color: transparent; border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: transparent">$649</td>
<td class="gt_row gt_center" headers="Trend"
style="border-left-width: 1px; border-left-style: solid; border-left-color: transparent; border-right-width: 1px; border-right-style: solid; border-right-color: transparent; border-top-width: 1px; border-top-style: solid; border-top-color: transparent; border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: transparent"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" class="svglite" width="85.04pt" height="14.17pt" viewbox="0 0 85.04 14.17">
<defs>
<style type="text/css">    .svglite line, .svglite polyline, .svglite polygon, .svglite path, .svglite rect, .svglite circle {      fill: none;      stroke: #000000;      stroke-linecap: round;      stroke-linejoin: round;      stroke-miterlimit: 10.00;    }    .svglite text {      white-space: pre;    }  </style>
</defs><rect width="100%" height="100%" style="stroke: none; fill: none;"></rect><defs>
<clippath id="cpMC4wMHw4NS4wNHwwLjAwfDE0LjE3">
<rect x="0.00" y="0.00" width="85.04" height="14.17"></rect>
</clippath></defs><g clip-path="url(#cpMC4wMHw4NS4wNHwwLjAwfDE0LjE3)"><polyline points="3.87,12.05 42.52,12.14 81.17,12.34 " style="stroke-width: 1.07; stroke-linecap: butt;"></polyline><circle cx="81.17" cy="12.34" r="0.89" style="stroke-width: 0.71; stroke: none;"></circle><circle cx="81.17" cy="12.34" r="0.89" style="stroke-width: 0.71; stroke: none;"></circle><circle cx="3.87" cy="12.05" r="0.89" style="stroke-width: 0.71; stroke: none;"></circle></g>
</svg></td>
</tr>
<tr class="even">
<td class="gt_row gt_left" headers="Country"
style="border-left-width: 1px; border-left-style: solid; border-left-color: transparent; border-right-width: 1px; border-right-style: solid; border-right-color: transparent; border-top-width: 1px; border-top-style: solid; border-top-color: transparent; border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: transparent">Albania</td>
<td class="gt_row gt_right" headers="1952"
style="border-left-width: 1px; border-left-style: solid; border-left-color: transparent; border-right-width: 1px; border-right-style: solid; border-right-color: transparent; border-top-width: 1px; border-top-style: solid; border-top-color: transparent; border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: transparent">$1,601</td>
<td class="gt_row gt_right" headers="1972"
style="border-left-width: 1px; border-left-style: solid; border-left-color: transparent; border-right-width: 1px; border-right-style: solid; border-right-color: transparent; border-top-width: 1px; border-top-style: solid; border-top-color: transparent; border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: transparent">$3,313</td>
<td class="gt_row gt_right" headers="1992"
style="border-left-width: 1px; border-left-style: solid; border-left-color: transparent; border-right-width: 1px; border-right-style: solid; border-right-color: transparent; border-top-width: 1px; border-top-style: solid; border-top-color: transparent; border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: transparent">$2,497</td>
<td class="gt_row gt_center" headers="Trend"
style="border-left-width: 1px; border-left-style: solid; border-left-color: transparent; border-right-width: 1px; border-right-style: solid; border-right-color: transparent; border-top-width: 1px; border-top-style: solid; border-top-color: transparent; border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: transparent"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" class="svglite" width="85.04pt" height="14.17pt" viewbox="0 0 85.04 14.17">
<defs>
<style type="text/css">    .svglite line, .svglite polyline, .svglite polygon, .svglite path, .svglite rect, .svglite circle {      fill: none;      stroke: #000000;      stroke-linecap: round;      stroke-linejoin: round;      stroke-miterlimit: 10.00;    }    .svglite text {      white-space: pre;    }  </style>
</defs><rect width="100%" height="100%" style="stroke: none; fill: none;"></rect><defs>
<clippath id="cpMC4wMHw4NS4wNHwwLjAwfDE0LjE3">
<rect x="0.00" y="0.00" width="85.04" height="14.17"></rect>
</clippath></defs><g clip-path="url(#cpMC4wMHw4NS4wNHwwLjAwfDE0LjE3)"><polyline points="3.87,10.26 42.52,6.54 81.17,8.31 " style="stroke-width: 1.07; stroke-linecap: butt;"></polyline><circle cx="81.17" cy="8.31" r="0.89" style="stroke-width: 0.71; stroke: none;"></circle><circle cx="3.87" cy="10.26" r="0.89" style="stroke-width: 0.71; stroke: none;"></circle><circle cx="42.52" cy="6.54" r="0.89" style="stroke-width: 0.71; stroke: none;"></circle></g>
</svg></td>
</tr>
<tr class="odd">
<td class="gt_row gt_left" headers="Country"
style="border-left-width: 1px; border-left-style: solid; border-left-color: transparent; border-right-width: 1px; border-right-style: solid; border-right-color: transparent; border-top-width: 1px; border-top-style: solid; border-top-color: transparent; border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: transparent">Algeria</td>
<td class="gt_row gt_right" headers="1952"
style="border-left-width: 1px; border-left-style: solid; border-left-color: transparent; border-right-width: 1px; border-right-style: solid; border-right-color: transparent; border-top-width: 1px; border-top-style: solid; border-top-color: transparent; border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: transparent">$2,449</td>
<td class="gt_row gt_right" headers="1972"
style="border-left-width: 1px; border-left-style: solid; border-left-color: transparent; border-right-width: 1px; border-right-style: solid; border-right-color: transparent; border-top-width: 1px; border-top-style: solid; border-top-color: transparent; border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: transparent">$4,183</td>
<td class="gt_row gt_right" headers="1992"
style="border-left-width: 1px; border-left-style: solid; border-left-color: transparent; border-right-width: 1px; border-right-style: solid; border-right-color: transparent; border-top-width: 1px; border-top-style: solid; border-top-color: transparent; border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: transparent; color: #FFA500; font-weight: bold">$5,023</td>
<td class="gt_row gt_center" headers="Trend"
style="border-left-width: 1px; border-left-style: solid; border-left-color: transparent; border-right-width: 1px; border-right-style: solid; border-right-color: transparent; border-top-width: 1px; border-top-style: solid; border-top-color: transparent; border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: transparent"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" class="svglite" width="85.04pt" height="14.17pt" viewbox="0 0 85.04 14.17">
<defs>
<style type="text/css">    .svglite line, .svglite polyline, .svglite polygon, .svglite path, .svglite rect, .svglite circle {      fill: none;      stroke: #000000;      stroke-linecap: round;      stroke-linejoin: round;      stroke-miterlimit: 10.00;    }    .svglite text {      white-space: pre;    }  </style>
</defs><rect width="100%" height="100%" style="stroke: none; fill: none;"></rect><defs>
<clippath id="cpMC4wMHw4NS4wNHwwLjAwfDE0LjE3">
<rect x="0.00" y="0.00" width="85.04" height="14.17"></rect>
</clippath></defs><g clip-path="url(#cpMC4wMHw4NS4wNHwwLjAwfDE0LjE3)"><polyline points="3.87,8.42 42.52,4.65 81.17,2.82 " style="stroke-width: 1.07; stroke-linecap: butt;"></polyline><circle cx="81.17" cy="2.82" r="0.89" style="stroke-width: 0.71; stroke: none;"></circle><circle cx="3.87" cy="8.42" r="0.89" style="stroke-width: 0.71; stroke: none;"></circle><circle cx="81.17" cy="2.82" r="0.89" style="stroke-width: 0.71; stroke: none;"></circle></g>
</svg></td>
</tr>
<tr class="even">
<td class="gt_row gt_left" headers="Country"
style="border-left-width: 1px; border-left-style: solid; border-left-color: transparent; border-right-width: 1px; border-right-style: solid; border-right-color: transparent; border-top-width: 1px; border-top-style: solid; border-top-color: transparent; border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: transparent">Angola</td>
<td class="gt_row gt_right" headers="1952"
style="border-left-width: 1px; border-left-style: solid; border-left-color: transparent; border-right-width: 1px; border-right-style: solid; border-right-color: transparent; border-top-width: 1px; border-top-style: solid; border-top-color: transparent; border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: transparent; color: #FFA500; font-weight: bold">$3,521</td>
<td class="gt_row gt_right" headers="1972"
style="border-left-width: 1px; border-left-style: solid; border-left-color: transparent; border-right-width: 1px; border-right-style: solid; border-right-color: transparent; border-top-width: 1px; border-top-style: solid; border-top-color: transparent; border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: transparent; color: #FFA500; font-weight: bold">$5,473</td>
<td class="gt_row gt_right" headers="1992"
style="border-left-width: 1px; border-left-style: solid; border-left-color: transparent; border-right-width: 1px; border-right-style: solid; border-right-color: transparent; border-top-width: 1px; border-top-style: solid; border-top-color: transparent; border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: transparent">$2,628</td>
<td class="gt_row gt_center" headers="Trend"
style="border-left-width: 1px; border-left-style: solid; border-left-color: transparent; border-right-width: 1px; border-right-style: solid; border-right-color: transparent; border-top-width: 1px; border-top-style: solid; border-top-color: transparent; border-bottom-width: 1px; border-bottom-style: solid; border-bottom-color: transparent"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" class="svglite" width="85.04pt" height="14.17pt" viewbox="0 0 85.04 14.17">
<defs>
<style type="text/css">    .svglite line, .svglite polyline, .svglite polygon, .svglite path, .svglite rect, .svglite circle {      fill: none;      stroke: #000000;      stroke-linecap: round;      stroke-linejoin: round;      stroke-miterlimit: 10.00;    }    .svglite text {      white-space: pre;    }  </style>
</defs><rect width="100%" height="100%" style="stroke: none; fill: none;"></rect><defs>
<clippath id="cpMC4wMHw4NS4wNHwwLjAwfDE0LjE3">
<rect x="0.00" y="0.00" width="85.04" height="14.17"></rect>
</clippath></defs><g clip-path="url(#cpMC4wMHw4NS4wNHwwLjAwfDE0LjE3)"><polyline points="3.87,6.09 42.52,1.84 81.17,8.03 " style="stroke-width: 1.07; stroke-linecap: butt;"></polyline><circle cx="81.17" cy="8.03" r="0.89" style="stroke-width: 0.71; stroke: none;"></circle><circle cx="81.17" cy="8.03" r="0.89" style="stroke-width: 0.71; stroke: none;"></circle><circle cx="42.52" cy="1.84" r="0.89" style="stroke-width: 0.71; stroke: none;"></circle></g>
</svg></td>
</tr>
</tbody>
</table>

</div>
