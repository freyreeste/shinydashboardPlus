# AdminLTE2 vertical progress bar

This creates a vertical progress bar.

## Usage

``` r
progressBar(
  value,
  min = 0,
  max = 100,
  vertical = FALSE,
  striped = FALSE,
  animated = FALSE,
  status = "primary",
  size = NULL,
  label = NULL
)
```

## Arguments

- value:

  Progress bar value. Must be between min and max.

- min:

  Progress bar minimum value (0 by default).

- max:

  Progress bar maximum value (100 by default).

- vertical:

  Progress vertical layout. Default to FALSE

- striped:

  Whether the progress is striped or not. FALSE by default.

- animated:

  Whether the progress is active or not. FALSE by default. Works only if
  striped is TRUE.

- status:

  Progress bar status. "primary" by default or "warning", "info",
  "danger" or "success". Valid statuses are defined as follows:

  - `primary`: \#3c8dbc

  - `success`: \#00a65a

  - `info`: \#00c0ef

  - `warning`: \#f39c12

  - `danger`: \#f56954

- size:

  Progress bar size. NULL by default: "sm", "xs" or "xxs" also
  available.

- label:

  Progress label. NULL by default.

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
      header = dashboardHeader(),
      sidebar = dashboardSidebar(),
      body = dashboardBody(
        box(
          title = "Horizontal",
          progressBar(
            value = 10,
            striped = TRUE,
            animated = TRUE,
            label = "10%"
          ),
          progressBar(
            value = 50,
            status = "warning",
            size = "xs"
          ),
          progressBar(
            value = 20,
            status = "danger",
            size = "sm"
          )
        ),
        box(
          title = "Vertical",
          progressBar(
            value = 10,
            striped = TRUE,
            animated = TRUE,
            vertical = TRUE
          ),
          progressBar(
            value = 50,
            status = "warning",
            size = "xs",
            vertical = TRUE
          ),
          progressBar(
            value = 20,
            status = "danger",
            size = "sm",
            vertical = TRUE
          )
        )
      ),
      title = "Progress bars"
    ),
    server = function(input, output) { }
  )
}
```
