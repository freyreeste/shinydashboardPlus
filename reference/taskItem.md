# Custom taskItem

Custom taskItem

## Usage

``` r
taskItem(text, value = 0, color = "aqua", href = NULL, inputId = NULL)
```

## Arguments

- text:

  The task text.

- value:

  A percent value to use for the bar.

- color:

  A color for the bar. Valid colors are listed in
  [validColors](https://rdrr.io/pkg/shinydashboard/man/validColors.html).

- href:

  An optional URL to link to.

- inputId:

  If not NULL, this item behaves like an action button.

## Examples

``` r
if (interactive()) {
  library(shiny)
  library(shinydashboard)
  library(shinydashboardPlus)

  shinyApp(
    ui = dashboardPage(
      dashboardHeader(
        dropdownMenu(
          type = "tasks",
          badgeStatus = "danger",
          taskItem(
            inputId = "mytask",
            value = 20,
            color = "aqua",
            text = "Click me!"
          ),
          taskItem(
            value = 40,
            color = "green",
            text = "Basic item"
          )
        )
      ),
      dashboardSidebar(),
      dashboardBody(),
      title = "Dashboard example"
    ),
    server = function(input, output) {
      observeEvent(input$mytask, {
        showModal(modalDialog(
          title = "Important message",
          "This is an important message!"
        ))
      })
    }
  )
}
```
