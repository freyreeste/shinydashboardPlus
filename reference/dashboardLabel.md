# AdminLTE2 label

Create a label

## Usage

``` r
dashboardLabel(..., status, style = "default")
```

## Arguments

- ...:

  any text.

- status:

  label status. Valid statuses are defined as follows:

  - `primary`: \#3c8dbc

  - `success`: \#00a65a

  - `info`: \#00c0ef

  - `warning`: \#f39c12

  - `danger`: \#f56954

- style:

  label border style: "default" (rounded angles), "circle" or "square".

## Author

David Granjon, <dgranjon@ymail.com>

## Examples

``` r
if (interactive()) {
  library(shiny)
  library(shinydashboard)
  library(shinydashboardPlus)

  shinyApp(
    ui = dashboardPage(
      dashboardHeader(),
      dashboardSidebar(),
      dashboardBody(
        dashboardLabel("Label 1", status = "info"),
        dashboardLabel("Label 2", status = "danger", style = "circle"),
        dashboardLabel("Label 3", status = "success", style = "square")
      )
    ),
    server = function(input, output) { }
  )
}
```
