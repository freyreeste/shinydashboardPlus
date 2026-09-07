# AdminLTE2 special large button

Create a large button ideal for web applications but identical to the
classic Shiny action button.

## Usage

``` r
appButton(..., inputId, label, icon = NULL, width = NULL)
```

## Arguments

- ...:

  Named attributes to be applied to the button or link.

- inputId:

  The `input` slot that will be used to access the value.

- label:

  The contents of the button or link–usually a text label, but you could
  also use any other HTML, like an image.

- icon:

  An optional [`icon()`](https://rdrr.io/pkg/shiny/man/icon.html) to
  appear on the button.

- width:

  The width of the input, e.g. `'400px'`, or `'100%'`; see
  [`validateCssUnit()`](https://rstudio.github.io/htmltools/reference/validateCssUnit.html).

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
      title = "App Buttons",
      status = NULL,
      appButton(
        inputId = "myAppButton",
        label = "Users", 
        icon = icon("users"), 
        dashboardBadge(textOutput("btnVal"), color = "blue")
      )
     )
    ),
    title = "App buttons"
  ),
  server = function(input, output) {
   output$btnVal <- renderText(input$myAppButton)
  }
 )
}
```
