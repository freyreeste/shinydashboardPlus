# Extra Skeleton Elements

## Extra template elements

[shinydashboard](https://rstudio.github.io/shinydashboard/) skeleton
elements are :

- [`dashboardPage()`](../reference/dashboardPage.md) (page wrapper)
- [`dashboardHeader()`](../reference/dashboardHeader.md) (navbar)
- [`dashboardSidebar()`](../reference/sidebar.md) (left sidebar)

However, AdminLTE has a footer and a right sidebar, also known as
controlbar. The footer is usually a good place to put contact
information like mail, authors and copyrights, while the controlbar may
contain secondary inputs or extra options that are not necessary to be
shown in the app.

### Controlbar

#### Basics

To include the controlbar, use
[`dashboardControlbar()`](../reference/controlbar.md) in the dedicated
*controlbar* parameter. It has several options:

- id is used to capture the current state of the controlbar (open or
  closed) and to programmatically toggle it with
  [`updateControlbar()`](../reference/controlbar.md). This is useful if
  the controlbar would have to open as a result of another action, to
  indicate users they have to play with it
- collapsed indicated whether the sidebar is opened or closed at start
- overlay controls the collapse behavior, that is whether the controlbar
  has to push the body content to the left. By default, it will cover
  the body content. Note that you may also control this behavior via the
  `dashboardPagge()` *option* parameter!
- skin is a cosmetic parameter with 2 values: dark or light with a
  default value to dark. Importantly, the global theme option do not
  impact the controlbar background

The app below will show an open controlbar at start.

``` r

library(shiny)
library(shinydashboard)
library(shinydashboardPlus)
shinyApp(
  ui = dashboardPage(
    header = dashboardHeader(),
    sidebar = dashboardSidebar(),
    body = dashboardBody(),
    controlbar = dashboardControlbar(collapsed = FALSE),
    title = "DashboardPage"
  ),
  server = function(input, output) { }
)
```

#### Include menus

The `dashboardControlbar` function also accepts to contain tabs,
similarly to the [`dashboardSidebar()`](../reference/sidebar.md)
navigation menu. [`controlbarMenu()`](../reference/controlbar.md) is a
modified
[`shiny::tabsetPanel()`](https://rdrr.io/pkg/shiny/man/tabsetPanel.html)
that has an optional *id* to control the select item on the server side
with [`updateControlbarMenu()`](../reference/controlbar.md). *selected*
indicates which item must be selected by default. Below is a use case of
the controlbar menu:

``` r

menu <- controlbarMenu(
  id = "controlbarMenu",
  controlbarItem(
    "Tab 1",
    "Welcome to tab 1"
  ),
  controlbarItem(
    "Tab 2",
    numericInput("num", "Observations:", 200, min = 1, max = 1000, step = 100)
  )
)

shinyApp(
  ui = dashboardPage(
    header = dashboardHeader(),
    sidebar = dashboardSidebar(),
    body = dashboardBody(),
    controlbar = dashboardControlbar(
      skin = "dark",
      menu
    ),
    title = "Right Sidebar"
  ),
  server = function(input, output) { }
)
```

It is best practice to limit the number of `controlbarItem` to 5 since
the horizontal space is rather limited.

#### The controlbar API

As mentioned above, the most powerful feature is the possibility to
control elements on the server. In the example below, the main sidebar
has 3 items, each item will open a specific menu item in the controlbar.

We first create 3 generic sidebar menu items using `lapply`. Note that
the controlbar menu is defined above in the previous example.

``` r

sidebarMenu(
  id = "sidebarMenu",
  lapply(1:3, function(i) {
    menuItem(
      sprintf("Menu %s", i), 
      tabName = sprintf("menu_%s", i), 
      icon = icon("circle")
    )
  })
)
```

`input$sidebarMenu` takes values in `menu_1`, `menu_2` and `menu_3`. On
the server side, we only recover the item index by splitting the input
value as follows `strsplit(input$sidebarMenu, "_")[[1]][2]`. Then we may
conditionally open the controlbar depending on the index value. The
update controlbar menu function will update the controlbar menu item
according to the index value, that is
`updateControlbarMenu("controlbarMenu", selected = idx)`.

To include even more interactivity, we listen to `input$controlbarMenu`.
When the second item is clicked, we toggle the box sidebar with
`updateBoxSidebar("boxSidebar")`.

In conclusion, you may imagine a lot of other situations.

Expand

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdib3g9IjAgMCAyNCAyNCIgc3R5bGU9ImhlaWdodDoxZW07d2lkdGg6MWVtO2ZpbGw6Y3VycmVudENvbG9yOyIgYXJpYS1oaWRkZW49InRydWUiIHJvbGU9ImltZyI+PHBhdGggZD0iTTIwIDVDMjAgNC40IDE5LjYgNCAxOSA0SDEzQzEyLjQgNCAxMiAzLjYgMTIgM0MxMiAyLjQgMTIuNCAyIDEzIDJIMjFDMjEuNiAyIDIyIDIuNCAyMiAzVjExQzIyIDExLjYgMjEuNiAxMiAyMSAxMkMyMC40IDEyIDIwIDExLjYgMjAgMTFWNVpNNCAxOUM0IDE5LjYgNC40IDIwIDUgMjBIMTFDMTEuNiAyMCAxMiAyMC40IDEyIDIxQzEyIDIxLjYgMTEuNiAyMiAxMSAyMkgzQzIuNCAyMiAyIDIxLjYgMiAyMVYxM0MyIDEyLjQgMi40IDEyIDMgMTJDMy42IDEyIDQgMTIuNCA0IDEzVjE5WiIgLz48L3N2Zz4=)

[Code](#controlbar)

``` r

shinyApp(
  ui = dashboardPage(
    header = dashboardHeader(),
    sidebar = dashboardSidebar(
      minified = TRUE, 
      collapsed = TRUE,
      sidebarMenu(
        id = "sidebarMenu",
        lapply(1:3, function(i) {
          menuItem(
            sprintf("Menu %s", i), 
            tabName = sprintf("menu_%s", i), 
            icon = icon("circle")
          )
        })
      )
    ),
    body = dashboardBody(
      tabItems(
        tabItem(tabName = "menu_1", "Content 1"), 
        tabItem(
          tabName = "menu_2",
          box(
            title = "Always the same plot!",
            collapsible = TRUE, 
            plotOutput("distPlot"),
            sidebar = boxSidebar(
              id = "boxSidebar",
              background = "#808080",
              width = "50%",
              sliderInput(
                "obs", 
                "Number of observations:",
                min = 0,
                max = 1000, 
                value = 500
              )
            )
          )
        )
      )
    ),
    controlbar = dashboardControlbar(
      id = "controlbar",
      menu
    ),
    title = "DashboardPage"
  ),
  server = function(input, output, session) {
    output$distPlot <- renderPlot({
      hist(rnorm(input$obs))
    })
    # Switch controlbar menu based on sidebar item value. Moreover
    # if the sidebar menu item is 2, the controlbar opens
    observeEvent(input$sidebarMenu, {
      idx <- strsplit(input$sidebarMenu, "_")[[1]][2]
      if (idx == 2) {
        updateControlbar("controlbar")
      }
      updateControlbarMenu("controlbarMenu", selected = idx)
    })
    
    # Clicking on the second controlbar item makes the box sidebar open
    observeEvent(input$controlbarMenu, {
      if (input$controlbarMenu == "Tab 2") updateBoxSidebar("boxSidebar")
    })
    
    observeEvent(input$num, {
      updateSliderInput(session, "obs", value = input$num)
    }, ignoreInit = TRUE)
    
  }
)
```

### Footer

Not surprisingly [`dashboardFooter()`](../reference/dashboardFooter.md)
creates a footer element. It has 2 slots, left and right, respectively.

``` r

shinyApp(
   ui = dashboardPage(
     header = dashboardHeader(),
     sidebar = dashboardSidebar(),
     body = dashboardBody(),
     footer = dashboardFooter(left = "Left content", right = "Right content"),
     title = "DashboardPage"
   ),
   server = function(input, output) { }
 )
```
