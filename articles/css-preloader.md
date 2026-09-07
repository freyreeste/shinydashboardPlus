# CSS preloaders

## How to set up a preloader?

Pass the argument `preloader` to the
[`dashboardPage()`](../reference/dashboardPage.md) function. It expects
a nested list containing all parameters necessary to
[`waiter::waiterShowOnLoad`](https://rdrr.io/pkg/waiter/man/waiter.html).
Please have a look to the [waiter](https://waiter.john-coene.com/)
[documentation](https://waiter.john-coene.com/) for more details.

That’s all!

Expand

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdib3g9IjAgMCAyNCAyNCIgc3R5bGU9ImhlaWdodDoxZW07d2lkdGg6MWVtO2ZpbGw6Y3VycmVudENvbG9yOyIgYXJpYS1oaWRkZW49InRydWUiIHJvbGU9ImltZyI+PHBhdGggZD0iTTIwIDVDMjAgNC40IDE5LjYgNCAxOSA0SDEzQzEyLjQgNCAxMiAzLjYgMTIgM0MxMiAyLjQgMTIuNCAyIDEzIDJIMjFDMjEuNiAyIDIyIDIuNCAyMiAzVjExQzIyIDExLjYgMjEuNiAxMiAyMSAxMkMyMC40IDEyIDIwIDExLjYgMjAgMTFWNVpNNCAxOUM0IDE5LjYgNC40IDIwIDUgMjBIMTFDMTEuNiAyMCAxMiAyMC40IDEyIDIxQzEyIDIxLjYgMTEuNiAyMiAxMSAyMkgzQzIuNCAyMiAyIDIxLjYgMiAyMVYxM0MyIDEyLjQgMi40IDEyIDMgMTJDMy42IDEyIDQgMTIuNCA0IDEzVjE5WiIgLz48L3N2Zz4=)

[Code](#preloader)

``` r

library(shiny)
library(shinydashboard)
library(shinydashboardPlus)
library(waiter)
shinyApp(
  ui = dashboardPage(
    preloader = list(html = tagList(spin_1(), "Loading ..."), color = "#3c8dbc"),
    header = dashboardHeader(),
    sidebar = dashboardSidebar(),
    body = dashboardBody(
      actionButton("reload", "Reload")
    ),
    title = "Preloader"
  ),
  server = function(input, output, session) {
    # fake reload
    observeEvent(input$reload, {
      session$reload()
    })
  }
)
```
