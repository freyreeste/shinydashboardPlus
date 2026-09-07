# AdminLTE2 todo list container

Create a todo list container. May be included in [box](box.md).

todoListItem creates a todo list item.

## Usage

``` r
todoList(..., sortable = TRUE)

todoListItem(..., checked = FALSE, label = NULL)
```

## Arguments

- ...:

  any element such as labels, ...

- sortable:

  Whether the list elements are sortable or not.

- checked:

  Whether the list item is checked or not.

- label:

  item label.

## Author

David Granjon, <dgranjon@ymail.com>

## Examples

``` r
if (interactive()) {
  library(shiny)
  library(shinydashboard)
  library(shinyjqui)
  library(shinydashboardPlus)

  shinyApp(
    ui = dashboardPage(
      dashboardHeader(),
      dashboardSidebar(),
      dashboardBody(
        box(
          "Sortable todo list demo",
          status = "warning",
          todoList(
            todoListItem(
              label = "Design a nice theme",
              "Some text here"
            ),
            todoListItem(
              label = "Make the theme responsive",
              "Some text here"
            ),
            todoListItem(
              checked = TRUE,
              label = "Let theme shine like a star"
            )
          )
        ),
        box(
          "Simple todo list demo",
          status = "warning",
          todoList(
            sortable = FALSE,
            todoListItem(
              label = "Design a nice theme",
              "Some text here"
            ),
            todoListItem(
              label = "Make the theme responsive",
              "Some text here"
            ),
            todoListItem(
              checked = TRUE,
              label = "Let theme shine like a star"
            )
          )
        )
      ),
      title = "Todo Lists"
    ),
    server = function(input, output) { }
  )
}
```
