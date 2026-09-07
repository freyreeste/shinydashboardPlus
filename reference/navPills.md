# AdminLTE2 nav pill container

navPills creates a container for nav elements. They are vertically
stacked. To insert in [box](box.md).

updateNavPills allows to programmatically change the currently selected
navPillsItem on the client.

navPillsItem creates a nav pill item.

## Usage

``` r
navPills(..., id = NULL)

updateNavPills(id, selected, session = shiny::getDefaultReactiveDomain())

navPillsItem(
  left = NULL,
  right = NULL,
  color = NULL,
  icon = NULL,
  selected = FALSE
)
```

## Arguments

- ...:

  slot for navPillsItem.

- id:

  navPills unique id to target.

- selected:

  Whether the item is active or not. FALSE by default.

- session:

  Shiny session object.

- left:

  pill left text.

- right:

  pill right text.

- color:

  pill color: see here for a list of valid colors
  <https://adminlte.io/themes/AdminLTE/pages/UI/general.html>. See
  below:

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

- icon:

  pill icon, if any.

## Author

David Granjon, <dgranjon@ymail.com>

## Examples

``` r

# navPills
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
          title = "Nav Pills",
          status = "info",
          "Box Body",
          footer = navPills(
            id = "pillItem",
            navPillsItem(
              left = "Item 1",
              color = "green",
              right = 10
            ),
            navPillsItem(
              left = "Item 2",
              color = "red",
              icon = icon("angle-down"),
              right = "10%",
              active = TRUE
            )
          )
        )
      ),
      title = "Nav Pills"
    ),
    server = function(input, output) {
      observeEvent(input$pillItem, {
        showNotification(sprintf("You clicked on pill N° %s", input$pillItem), type = "message")
      })
    }
  )
}


# update navPills
if (interactive()) {
  library(shiny)
  library(shinydashboard)
  library(shinydashboardPlus)

  shinyApp(
    ui = dashboardPage(
      dashboardHeader(),
      dashboardSidebar(),
      dashboardBody(
        radioButtons("controller", "Controller", choices = c(1, 2, 3)),
        br(),
        box(
          title = "Nav Pills",
          status = "info",
          "Box Body",
          footer = navPills(
            inputId = "pills",
            navPillsItem(
              left = "Item 1",
              color = "green",
              right = 10
            ),
            navPillsItem(
              left = "Item 2",
              color = "red",
              icon = icon("angle-down"),
              right = "10%"
            ),
            navPillsItem(
              left = "Item 3",
              color = "blue",
              icon = icon("angle-up"),
              right = "30%"
            )
          )
        )
      ),
      title = "Nav Pills"
    ),
    server = function(input, output, session) {
      observeEvent(input$controller, {
        updateNavPills(id = "pills", selected = input$controller)
      })
      observeEvent(input$pills, {
        showNotification(sprintf("You selected pill N° %s", input$pills), type = "message")
      })
    }
  )
}
```
