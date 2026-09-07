# AdminLTE2 badge

Create a badge. It may be inserted in any element like inside a
[actionButton](https://rdrr.io/pkg/shiny/man/actionButton.html) or a
[dashboardSidebar](sidebar.md).

## Usage

``` r
dashboardBadge(..., color)
```

## Arguments

- ...:

  Any html text element.

- color:

  label color. See below:

  - `light-blue (primary status)`: \#3c8dbc .

  - `red (danger status)`: \#dd4b39 .

  - `green (success status)`: \#00a65a .

  - `aqua (info status)`: \#00c0ef .

  - `yellow (warning status)`: \#f39c12 .

  - `blue`: \#0073b7 .

  - `navy`: \#001F3F .

  - `teal`: \#39CCCC .

  - `olive`: \#3D9970 .

  - `lime`: \#01FF70 .

  - `orange`: \#FF851B .

  - `fuchsia`: \#F012BE .

  - `purple`: \#605ca8 .

  - `maroon`: \#D81B60 .

  - `black`: \#111 .

  - `gray`: \#d2d6de .

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
        dashboardBadge("Badge 1", color = "blue"),
        actionButton(
          inputId = "badge",
          label = "Hello",
          icon = NULL,
          width = NULL,
          dashboardBadge(1, color = "orange")
        )
      )
    ),
    server = function(input, output) { }
  )
}
```
