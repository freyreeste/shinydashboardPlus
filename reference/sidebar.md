# Create a dashboard sidebar.

A dashboard sidebar typically contains a
[`sidebarMenu`](https://rdrr.io/pkg/shinydashboard/man/sidebarMenu.html),
although it may also contain a
[`sidebarSearchForm`](https://rdrr.io/pkg/shinydashboard/man/sidebarSearchForm.html),
or other Shiny inputs.

updateSidebar allows to toggle a dashboardSidebar on the client.

## Usage

``` r
dashboardSidebar(
  ...,
  disable = FALSE,
  width = NULL,
  collapsed = FALSE,
  minified = TRUE,
  id = NULL
)

updateSidebar(id, session = shiny::getDefaultReactiveDomain())
```

## Arguments

- ...:

  Items to put in the sidebar.

- disable:

  If `TRUE`, the sidebar will be disabled.

- width:

  The width of the sidebar. This must either be a number which specifies
  the width in pixels, or a string that specifies the width in CSS
  units.

- collapsed:

  If `TRUE`, the sidebar will be collapsed on app startup.

- minified:

  Whether to slightly close the sidebar but still show item icons.
  Default to TRUE.

- id:

  Sidebar id.

- session:

  Shiny session object.

## Examples

``` r
if (interactive()) {
 library(shiny)
 library(shinydashboard)
 library(shinydashboardPlus)
 
 shinyApp(
   ui = dashboardPage(
     header = dashboardHeader(),
     sidebar = dashboardSidebar(id = "sidebar"),
     body = dashboardBody(
       actionButton(inputId = "sidebarToggle", label = "Toggle Sidebar")
     )
   ),
   server = function(input, output, session) {
     
     observeEvent(input$sidebar, {
       if (input$sidebar) {
         showModal(modalDialog(
           title = "Alert",
           "The sidebar is opened.",
           easyClose = TRUE,
           footer = NULL
         ))
       }
     })
     
     observeEvent(input$sidebarToggle, {
       updateSidebar("sidebar")
     })
     
     observe({
       print(input$sidebar)
     })
   }
 )
}
```
