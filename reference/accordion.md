# AdminLTE2 accordion container

Create an accordion container. Accordions are part of collapsible
elements.

accordionItem creates an accordion item to put inside an accordion
container.

updateAccordion toggles an accordion on the client.

## Usage

``` r
accordion(..., id = NULL, width = 12)

accordionItem(..., title, status = NULL, collapsed = TRUE, solidHeader = TRUE)

updateAccordion(id, selected, session = shiny::getDefaultReactiveDomain())
```

## Arguments

- ...:

  slot for accordionItem.

- id:

  Accordion to target.

- width:

  The width of the accordion.

- title:

  Optional title.

- status:

  The status of the item This determines the item's background color.
  Valid statuses are defined as follows:

  - `primary`: \#3c8dbc

  - `success`: \#00a65a

  - `info`: \#00c0ef

  - `warning`: \#f39c12

  - `danger`: \#f56954

  - `navy`: \#001F3F

  - `teal`: \#39CCCC

  - `purple`: \#605ca8

  - `orange`: \#ff851b

  - `maroon`: \#D81B60

  - `black`: \#111111

  Only primary, success, info, warning and danger are compatible with
  solidHeader!

- collapsed:

  If TRUE, start collapsed. This must be used with `collapsible=TRUE`.

- solidHeader:

  Should the header be shown with a solid color background?

- selected:

  Index of the newly selected accordionItem.

- session:

  Shiny session object.

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
        accordion(
          id = "accordion1",
          accordionItem(
            title = "Accordion 1 Item 1",
            status = "danger",
            collapsed = TRUE,
            "This is some text!"
          ),
          accordionItem(
            title = "Accordion 1 Item 2",
            status = "warning",
            collapsed = FALSE,
            "This is some text!"
          )
        ),
        accordion(
          id = "accordion2",
          accordionItem(
            title = "Accordion 2 Item 1",
            status = "info",
            collapsed = TRUE,
            "This is some text!"
          ),
          accordionItem(
            title = "Accordion 2 Item 2",
            status = "success",
            collapsed = FALSE,
            "This is some text!"
          )
        )
      ),
      title = "Accordion"
    ),
    server = function(input, output) { }
  )
}


# Update accordion
if (interactive()) {
  library(shiny)
  library(shinydashboard)
  library(shinydashboardPlus)

  shinyApp(
    ui = dashboardPage(
      dashboardHeader(),
      dashboardSidebar(),
      dashboardBody(
        radioButtons("controller", "Controller", choices = c(1, 2)),
        br(),
        accordion(
          id = "accordion1",
          accordionItem(
            title = "Accordion 1 Item 1",
            status = "danger",
            collapsed = TRUE,
            "This is some text!"
          ),
          accordionItem(
            title = "Accordion 1 Item 2",
            status = "warning",
            collapsed = TRUE,
            "This is some text!"
          )
        )
      ),
      title = "Update Accordion"
    ),
    server = function(input, output, session) {
      observeEvent(input$controller, {
        updateAccordion(id = "accordion1", selected = input$controller)
      })
      observe(print(input$accordion1))
      observeEvent(input$accordion1, {
        showNotification(
          sprintf("You selected accordion N° %s", input$accordion1),
          type = "message"
        )
      })
    }
  )
}
```
