# Dashboard Footer

This creates a dashboard footer

## Usage

``` r
dashboardFooter(left = NULL, right = NULL)
```

## Arguments

- left:

  Left text.

- right:

  Right text.

## Examples

``` r
if (interactive()) {
library(shiny)
library(shinydashboard)
library(shinydashboardPlus)

shinyApp(
  ui = dashboardPage(
    header = dashboardHeader(),
    sidebar = dashboardSidebar(),
    body = dashboardBody(),
    footer = dashboardFooter(
     left = "By Divad Nojnarg",
     right = "Zurich, 2019"
    ),
    title = "DashboardPage"
  ),
  server = function(input, output) { }
)
}
```
