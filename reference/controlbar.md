# AdminLTE2 dashboard right sidebar

dashboardControlbar create a right sidebar container.

updateControlbar allows to toggle a dashboardControlbar.

controlbarMenu is a tabset panel for the dashboardControlbar.

controlbarItem is a tabPanel for the controlbarMenu.

updateControlbarMenu allows to programmatically change the currently
selected controlbarItem on the client.

## Usage

``` r
dashboardControlbar(
  ...,
  id = NULL,
  disable = FALSE,
  width = 230,
  collapsed = TRUE,
  overlay = TRUE,
  skin = "dark",
  .list = NULL
)

updateControlbar(id, session = shiny::getDefaultReactiveDomain())

controlbarMenu(..., id = NULL, selected = NULL)

controlbarItem(title, ..., value = title, icon = NULL)

updateControlbarMenu(
  id,
  selected = NULL,
  session = shiny::getDefaultReactiveDomain()
)
```

## Arguments

- ...:

  slot for controlbarMenu. Not compatible with .items.

- id:

  Controlbar id.

- disable:

  If `TRUE`, the sidebar will be disabled.

- width:

  Sidebar width in pixels. Numeric value expected. 230 by default.

- collapsed:

  Whether the control bar on the right side is collapsed or not at
  start. TRUE by default.

- overlay:

  Whether the sidebar covers the content when expanded. Default to TRUE.

- skin:

  background color: "dark" or "light".

- .list:

  Pass element here if you do not want to embed them in panels. Not
  compatible with ...

- session:

  Shiny session object.

- selected:

  Item to select.

- title:

  Display title for tab

- value:

  The value that should be sent when `tabsetPanel` reports that this tab
  is selected. If omitted and `tabsetPanel` has an `id`, then the title
  will be used.

- icon:

  Optional icon to appear on the tab. This attribute is only valid when
  using a `tabPanel` within a
  [`navbarPage()`](https://rdrr.io/pkg/shiny/man/navbarPage.html).

## Note

Until a maximum of 5 controlbarItem! AdminLTE 2 does not support more
panels.

## Author

David Granjon, <dgranjon@ymail.com>

## Examples

``` r

# Controlbar example
if (interactive()) {
 library(shiny)
 library(shinydashboard)
 library(shinydashboardPlus)
 shinyApp(
   ui = dashboardPage(
     header = dashboardHeader(),
     sidebar = dashboardSidebar(),
     body = dashboardBody(),
     controlbar = dashboardControlbar(
      skin = "dark",
      controlbarMenu(
       id = "menu",
       controlbarItem(
        "Tab 1",
        "Welcome to tab 1"
       ),
       controlbarItem(
        "Tab 2",
        "Welcome to tab 2"
       )
      )
     ),
     title = "Right Sidebar"
   ),
   server = function(input, output) { }
 )
}

# Toggle the dashboard controlbar
if (interactive()) {
 library(shiny)
 library(shinydashboard)
 library(shinydashboardPlus)
 
 shinyApp(
   ui = dashboardPage(
     header = dashboardHeader(),
     sidebar = dashboardSidebar(),
     body = dashboardBody(
       actionButton(inputId = "controlbarToggle", label = "Toggle Controlbar")
     ),
     controlbar = dashboardControlbar(id = "controlbar")
   ),
   server = function(input, output, session) {
     
     observeEvent(input$controlbar, {
       if (input$controlbar) {
         showModal(modalDialog(
           title = "Alert",
           "The controlbar is opened.",
           easyClose = TRUE,
           footer = NULL
         ))
       }
     })
     
     observeEvent(input$controlbarToggle, {
       updateControlbar("controlbar")
     })
     
     observe({
       print(input$controlbar)
     })
   }
 )
}

# controlbar with controlbarMenu
if (interactive()) {
 library(shiny)
 library(shinydashboard)
 library(shinydashboardPlus)
 
 shinyApp(
   ui = dashboardPage(
     header = dashboardHeader(),
     sidebar = dashboardSidebar(),
     body = dashboardBody(),
     controlbar = dashboardControlbar(
      id = "controlbar",
      controlbarMenu(
       id = "menu",
       controlbarItem(
        "Tab 1",
        "Welcome to tab 1"
       ),
       controlbarItem(
        "Tab 2",
        "Welcome to tab 2"
       )
      )
     )
   ),
   server = function(input, output, session) {
     
     observeEvent(input$menu, {
       showModal(modalDialog(
         title = "Alert",
         sprintf(" %s is active", input$menu),
         easyClose = TRUE,
         footer = NULL
       ))
     })
   }
 )
}

# Update a controlbar menu
if (interactive()) {
 library(shiny)
 library(shinydashboard)
 library(shinydashboardPlus)
 
 shinyApp(
   ui = dashboardPage(
     header = dashboardHeader(),
     sidebar = dashboardSidebar(),
     body = dashboardBody(
      radioButtons("controller", "Controller", choices = c(1, 2, 3))
     ),
     controlbar = dashboardControlbar(
      id = "controlbar",
      controlbarMenu(
       id = "menu",
       controlbarItem(
         paste0("Tab", 1),
         paste("Welcome to tab", 1)
       ),
       controlbarItem(
         paste0("Tab", 2),
         paste("Welcome to tab", 2)
       ),
       controlbarItem(
         paste0("Tab", 3),
         paste("Welcome to tab", 3)
       )
      )
     )
   ),
   server = function(input, output, session) {
    observeEvent(input$controller, {
     updateControlbarMenu(
      "menu", 
      selected = paste0("Tab", input$controller)
     )
    })
   }
 )
}
```
