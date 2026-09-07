# A flipBox based on the W3C example

flipBox creates a box that flips from back to front and inversely

updateFlipBox programmatically toggles a flipBox from the server.

## Usage

``` r
flipBox(id, front, back, trigger = c("click", "hover"), width = 6)

updateFlipBox(id, session = shiny::getDefaultReactiveDomain())
```

## Arguments

- id:

  flipBox id.

- front:

  ui for the front of the flip box

- back:

  ui for the back of the flip box

- trigger:

  How to trigger rotate effect. Either click or hover. Default to click.

- width:

  flipbox width. Between 1 and 12.

- session:

  Shiny session object.

## Details

To access the state of the flipbox use the input alias `input$<id>`. For
example, if your flipBox's id is myawesomeflipbox, you can access its
state via `input$myawesomeflipbox` where TRUE corresponds to the front,
FALSE to the back.

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
      fluidRow(
        column(
          width = 6,
          uiOutput("active_side"), 
          flipBox(
            id = "myflipbox", 
            trigger = "hover",
            width = 12,
            front = div(
              class = "text-center",
              h1("Flip on hover"),
              img(
                src = "https://image.flaticon.com/icons/svg/149/149076.svg",
                height = "300px",
                width = "100%"
              )
            ),
            back = div(
              class = "text-center",
              height = "300px",
              width = "100%",
              h1("Flip on hover"),
              p("More information....")
            )
          )
        ),
        column(
          width = 6,
          uiOutput("active_side_2"),
          flipBox(
            id = "myflipbox2",
            width = 12,
            front = div(
              class = "text-center",
              h1("Flip on click"),
              img(
                src = "https://image.flaticon.com/icons/svg/149/149076.svg",
                height = "300px",
                width = "100%"
              )
            ),
            back = div(
              class = "text-center",
              height = "300px",
              width = "100%",
              h1("Flip on click"),
              p("More information....")
            )
          )
        )
      )
    )
  ),
  
  server = function(input, output, session) {
    output$active_side <- renderUI({
      side <- if (input$myflipbox) "front" else "back"
      dashboardBadge(side, color = "blue")
    })
    
    output$active_side_2<- renderUI({
      side <- if (input$myflipbox2) "front" else "back"
      dashboardBadge(side, color = "blue")
    })
  }
 )
}
if (interactive()) {
 library(shiny)
 library(shinydashboard)
 library(shinydashboardPlus)
 shinyApp(
   ui = dashboardPage(
     dashboardHeader(),
     dashboardSidebar(),
     dashboardBody(
       actionButton("toggle", "Toggle flip box"),
       uiOutput("active_side"), 
       flipBox(
         id = "myflipbox",
         front = div(
           class = "text-center",
           img(
             src = "https://image.flaticon.com/icons/svg/149/149076.svg",
             height = "300px",
             width = "100%"
           )
         ),
         back = div(
           class = "text-center",
           height = "300px",
           width = "100%",
           h1("Details...."),
           p("More information....")
         )
       )
     )
   ),
   
   server = function(input, output, session) {
    output$active_side <- renderUI({
     side <- if (input$myflipbox) "front" else "back"
     dashboardBadge(side, color = "blue")
    })
    
    observeEvent(input$toggle, {
     updateFlipBox("myflipbox")
    })
   }
 )
}
```
