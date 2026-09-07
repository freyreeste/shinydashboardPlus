# AdminLTE2 block quote

If you want to quote text

## Usage

``` r
blockQuote(..., side = "left")
```

## Arguments

- ...:

  any element.

- side:

  blockquote orientation. "left" by default, can be set to "right".

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
          title = "BlockQuote example",
          blockQuote("I quote some text here!"),
          blockQuote("I quote some text here!", side = "right")
        )
      ),
      title = "blockQuote"
    ),
    server = function(input, output) { }
  )
}
```
