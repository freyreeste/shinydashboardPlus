# AdminLTE2 starBlock

Create a starBlock item (ideal for rating)

## Usage

``` r
starBlock(value, max = 5, color = "yellow")
```

## Arguments

- value:

  Current score. Should be positive and lower or equal to max.

- max:

  Maximum number of stars by block.

- color:

  Star color: see [`validColors()`](validColors.md) in the
  documentation. See below:

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
        box(
          title = "Star example",
          starBlock(5),
          starBlock(5, color = "olive"),
          starBlock(1, color = "maroon"),
          starBlock(3, color = "teal")
        )
      ),
      title = "starBlock"
    ),
    server = function(input, output) { }
  )
}
```
