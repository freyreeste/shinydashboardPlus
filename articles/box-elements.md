# Box Elements

## Boxes components

[shinydashboardPlus](https://github.com/RinteRface/shinydashboardPlus)
brings tons of new elements to include in boxes or elsewhere. Some of
them has partially been described in the previous vignette.

  

[Go to previous vignette](improved-boxes.md)

### Description Block

[`descriptionBlock()`](../reference/box.md) is a sub-container that may
be included in any [`box()`](../reference/box.md). It is convenient to
display metrics.

Expand

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdib3g9IjAgMCAyNCAyNCIgc3R5bGU9ImhlaWdodDoxZW07d2lkdGg6MWVtO2ZpbGw6Y3VycmVudENvbG9yOyIgYXJpYS1oaWRkZW49InRydWUiIHJvbGU9ImltZyI+PHBhdGggZD0iTTIwIDVDMjAgNC40IDE5LjYgNCAxOSA0SDEzQzEyLjQgNCAxMiAzLjYgMTIgM0MxMiAyLjQgMTIuNCAyIDEzIDJIMjFDMjEuNiAyIDIyIDIuNCAyMiAzVjExQzIyIDExLjYgMjEuNiAxMiAyMSAxMkMyMC40IDEyIDIwIDExLjYgMjAgMTFWNVpNNCAxOUM0IDE5LjYgNC40IDIwIDUgMjBIMTFDMTEuNiAyMCAxMiAyMC40IDEyIDIxQzEyIDIxLjYgMTEuNiAyMiAxMSAyMkgzQzIuNCAyMiAyIDIxLjYgMiAyMVYxM0MyIDEyLjQgMi40IDEyIDMgMTJDMy42IDEyIDQgMTIuNCA0IDEzVjE5WiIgLz48L3N2Zz4=)

[Code](#description-block)

``` r

library(shiny)
library(shinydashboard)
library(shinydashboardPlus)
 shinyApp(
  ui = dashboardPage(
    dashboardHeader(),
    dashboardSidebar(),
    dashboardBody(
     box(
      solidHeader = FALSE,
      title = "Status summary",
      background = NULL,
      width = 4,
      status = "danger",
      footer = fluidRow(
        column(
          width = 6,
          descriptionBlock(
            number = "17%", 
            numberColor = "green", 
            numberIcon = icon("caret-up"),
            header = "$35,210.43", 
            text = "TOTAL REVENUE", 
            rightBorder = TRUE,
            marginBottom = FALSE
          )
        ),
        column(
          width = 6,
          descriptionBlock(
            number = "18%", 
            numberColor = "red", 
            numberIcon = icon("caret-down"),
            header = "1200", 
            text = "GOAL COMPLETION", 
            rightBorder = FALSE,
            marginBottom = FALSE
          )
        )
      )
     )
    ),
    title = "Description Block"
  ),
  server = function(input, output) { }
 )
```

### Coming soon …
