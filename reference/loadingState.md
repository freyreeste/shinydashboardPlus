# AdminLTE2 loading state element

When a section is still work in progress or a computation is running

## Usage

``` r
loadingState()
```

## Note

Loading state can be programmatically used when a conputation is running
for instance.

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
          title = "loading spinner",
          loadingState()
        )
      ),
      title = "Loading State"
    ),
    server = function(input, output) { }
  )
}
```
