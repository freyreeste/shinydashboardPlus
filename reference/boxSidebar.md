# Create a sidebar for a box

boxSidebar is inserted in the sidebar slot of [box](box.md).

updateBoxSidebar toggle a boxSidebar on the client.

## Usage

``` r
boxSidebar(
  ...,
  id = NULL,
  width = 50,
  background = "#333a40",
  startOpen = FALSE,
  icon = shiny::icon("gears")
)

updateBoxSidebar(id, session = shiny::getDefaultReactiveDomain())
```

## Arguments

- ...:

  Sidebar content.

- id:

  Sidebar id.

- width:

  Sidebar opening width in percentage. 50% by default, means the card
  sidebar will take 50 A numeric value between 25 and 100.

- background:

  Sidebar background color. Dark by default. Expect a HEX code.

- startOpen:

  Whether the sidebar is open at start. FALSE by default.

- icon:

  Sidebar icon. Expect
  [`icon`](https://rdrr.io/pkg/shiny/man/icon.html).

- session:

  Shiny session object.

## Examples

``` r

# Toggle a box sidebar
if (interactive()) {
 library(shiny)
 library(shinydashboard)
 library(shinydashboardPlus)
 
 shinyApp(
  ui = dashboardPage(
    header = dashboardHeader(),
    body = dashboardBody(
      box(
        title = "Update box sidebar", 
        closable = TRUE, 
        width = 12,
        height = "500px",
        solidHeader = FALSE, 
        collapsible = TRUE,
        actionButton("update", "Toggle card sidebar"),
        sidebar = boxSidebar(
          id = "mycardsidebar",
          p("Sidebar Content")
        )
      )
    ),
    sidebar = dashboardSidebar()
  ),
  server = function(input, output, session) {
    observe(print(input$mycardsidebar))
    
    observeEvent(input$update, {
      updateBoxSidebar("mycardsidebar")
    })
    
  }
 )
}
```
