# Improved Skins

## A Real Time Skin Selector

[shinydashboardPlus](https://github.com/RinteRface/shinydashboardPlus)
has a new feature called the
[`skinSelector()`](../reference/skinSelector.md). This is a JavaScript
based widget allowing the end user to change the app skin. According to
the [`dashboardPage()`](../reference/dashboardPage.md), there are 6
unique colors with 2 versions, light or dark. Note that the
[`dashboardControlbar()`](../reference/controlbar.md) is the perfect
place to host the [`skinSelector()`](../reference/skinSelector.md) since
it may be seen as a secondary input (your app may still work without :))

Expand

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdib3g9IjAgMCAyNCAyNCIgc3R5bGU9ImhlaWdodDoxZW07d2lkdGg6MWVtO2ZpbGw6Y3VycmVudENvbG9yOyIgYXJpYS1oaWRkZW49InRydWUiIHJvbGU9ImltZyI+PHBhdGggZD0iTTIwIDVDMjAgNC40IDE5LjYgNCAxOSA0SDEzQzEyLjQgNCAxMiAzLjYgMTIgM0MxMiAyLjQgMTIuNCAyIDEzIDJIMjFDMjEuNiAyIDIyIDIuNCAyMiAzVjExQzIyIDExLjYgMjEuNiAxMiAyMSAxMkMyMC40IDEyIDIwIDExLjYgMjAgMTFWNVpNNCAxOUM0IDE5LjYgNC40IDIwIDUgMjBIMTFDMTEuNiAyMCAxMiAyMC40IDEyIDIxQzEyIDIxLjYgMTEuNiAyMiAxMSAyMkgzQzIuNCAyMiAyIDIxLjYgMiAyMVYxM0MyIDEyLjQgMi40IDEyIDMgMTJDMy42IDEyIDQgMTIuNCA0IDEzVjE5WiIgLz48L3N2Zz4=)

[Code](#skin-selector)

``` r

library(shiny)
library(shinydashboard)
library(shinydashboardPlus)
shinyApp(
   ui = dashboardPage(
     header = dashboardHeader(),
     sidebar = dashboardSidebar(),
     body = dashboardBody(),
     controlbar = dashboardControlbar(collapsed = FALSE, skinSelector()),
     title = "Skin Selector"
   ),
   server = function(input, output) { }
 )
```

## A New Dark Skin: midnight

The midnight theme is powered by the corresponding Github
[project](https://github.com/anvyst/adminlte-skin-midnight). It provides
a plug and play dark theme.

Expand

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdib3g9IjAgMCAyNCAyNCIgc3R5bGU9ImhlaWdodDoxZW07d2lkdGg6MWVtO2ZpbGw6Y3VycmVudENvbG9yOyIgYXJpYS1oaWRkZW49InRydWUiIHJvbGU9ImltZyI+PHBhdGggZD0iTTIwIDVDMjAgNC40IDE5LjYgNCAxOSA0SDEzQzEyLjQgNCAxMiAzLjYgMTIgM0MxMiAyLjQgMTIuNCAyIDEzIDJIMjFDMjEuNiAyIDIyIDIuNCAyMiAzVjExQzIyIDExLjYgMjEuNiAxMiAyMSAxMkMyMC40IDEyIDIwIDExLjYgMjAgMTFWNVpNNCAxOUM0IDE5LjYgNC40IDIwIDUgMjBIMTFDMTEuNiAyMCAxMiAyMC40IDEyIDIxQzEyIDIxLjYgMTEuNiAyMiAxMSAyMkgzQzIuNCAyMiAyIDIxLjYgMiAyMVYxM0MyIDEyLjQgMi40IDEyIDMgMTJDMy42IDEyIDQgMTIuNCA0IDEzVjE5WiIgLz48L3N2Zz4=)

[Code](#skin-midnight)

``` r

library(shiny)
library(shinydashboard)
library(shinydashboardPlus)

shinyApp(
   ui = dashboardPage(
     skin = "midnight",
     header = dashboardHeader(),
     sidebar = dashboardSidebar(),
     body = dashboardBody(
       box(
         title = "My box"
       )
     ),
     controlbar = dashboardControlbar(),
     footer = dashboardFooter(),
     title = "Midnight Skin"
   ),
   server = function(input, output) { }
 )
```

![Midnight skin overview](figures/skin-midnight-overview.png)

Midnight skin overview

This is the fastest option to get a dark design. You’ll see below that
the [fresh](https://github.com/dreamRs/fresh) package is able to provide
a similar look and feel, with much more options (but more effort).

Important: this feature is still **experimental lifecycle**!

## Material Design + AdminLTE

To activate the material design feature, set *md* to TRUE in
[`dashboardPage()`](../reference/dashboardPage.md). This feature is
powered by
[MaterialAdminLTE](https://github.com/DucThanhNguyen/MaterialAdminLTE),
built on top of AdminLTE2 and [material design for Bootstrap
3](https://fezvrasta.github.io/bootstrap-material-design/)
**experimental lifecycle**!

Expand

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdib3g9IjAgMCAyNCAyNCIgc3R5bGU9ImhlaWdodDoxZW07d2lkdGg6MWVtO2ZpbGw6Y3VycmVudENvbG9yOyIgYXJpYS1oaWRkZW49InRydWUiIHJvbGU9ImltZyI+PHBhdGggZD0iTTIwIDVDMjAgNC40IDE5LjYgNCAxOSA0SDEzQzEyLjQgNCAxMiAzLjYgMTIgM0MxMiAyLjQgMTIuNCAyIDEzIDJIMjFDMjEuNiAyIDIyIDIuNCAyMiAzVjExQzIyIDExLjYgMjEuNiAxMiAyMSAxMkMyMC40IDEyIDIwIDExLjYgMjAgMTFWNVpNNCAxOUM0IDE5LjYgNC40IDIwIDUgMjBIMTFDMTEuNiAyMCAxMiAyMC40IDEyIDIxQzEyIDIxLjYgMTEuNiAyMiAxMSAyMkgzQzIuNCAyMiAyIDIxLjYgMiAyMVYxM0MyIDEyLjQgMi40IDEyIDMgMTJDMy42IDEyIDQgMTIuNCA0IDEzVjE5WiIgLz48L3N2Zz4=)

[Code](#material-skin)

``` r

library(shiny)
library(shinydashboard)
library(shinydashboardPlus)

shinyApp(
   ui = dashboardPage(
     md = TRUE,
     skin = "blue",
     header = dashboardHeader(),
     sidebar = dashboardSidebar(),
     body = dashboardBody(
       box(title = "My box")
     ),
     controlbar = dashboardControlbar(),
     footer = dashboardFooter(),
     title = "Material design"
   ),
   server = function(input, output) { }
 )
```

## Fresh

[`{fresh}`](https://dreamrs.github.io/fresh/index.html) is developed by
the [dreamRs](https://www.dreamrs.fr/) team. It is built on top of
[sass](https://rstudio.github.io/sass/), which provides a solid R
[API](https://github.com/rstudio/sass) to write SASS variables and
compile into CSS. [fresh](https://github.com/dreamRs/fresh) captures
most of the AdminLTE2 (as well as AdminLTE3 for Bootstrap 4) SASS
variables to allow deep customization, hiding all the compilation burden
under the hood.

[`adminlte_color()`](https://rdrr.io/pkg/fresh/man/adminlte_color.html)
provides an interface to all available AdminLTE colors and allow to
overwrite the default. I strongly suggest to avoid setting the default
green to blue, as it might become confusing. Instead, it is better to
play with color palettes. Similarly, `adminlte_sidebar` allows to
re-style the sidebar component. The fresh theme below is based on some
cyberpunk color palettes.

Expand

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdib3g9IjAgMCAyNCAyNCIgc3R5bGU9ImhlaWdodDoxZW07d2lkdGg6MWVtO2ZpbGw6Y3VycmVudENvbG9yOyIgYXJpYS1oaWRkZW49InRydWUiIHJvbGU9ImltZyI+PHBhdGggZD0iTTIwIDVDMjAgNC40IDE5LjYgNCAxOSA0SDEzQzEyLjQgNCAxMiAzLjYgMTIgM0MxMiAyLjQgMTIuNCAyIDEzIDJIMjFDMjEuNiAyIDIyIDIuNCAyMiAzVjExQzIyIDExLjYgMjEuNiAxMiAyMSAxMkMyMC40IDEyIDIwIDExLjYgMjAgMTFWNVpNNCAxOUM0IDE5LjYgNC40IDIwIDUgMjBIMTFDMTEuNiAyMCAxMiAyMC40IDEyIDIxQzEyIDIxLjYgMTEuNiAyMiAxMSAyMkgzQzIuNCAyMiAyIDIxLjYgMiAyMVYxM0MyIDEyLjQgMi40IDEyIDMgMTJDMy42IDEyIDQgMTIuNCA0IDEzVjE5WiIgLz48L3N2Zz4=)

[Code](#fresh)

``` r

library(fresh)
# create the theme with a cyberpunk color palette
theme <- create_theme(
  adminlte_color(
    green = "#3fff2d",
    blue = "#2635ff",
    red = " #ff2b2b",
    yellow = "#feff6e",
    fuchsia = "#ff5bf8",
    navy = "#374c92",
    purple = "#615cbf",
    maroon = "#b659c9",
    light_blue = "#5691cc"
  ),
  adminlte_sidebar(
    dark_bg = "#D8DEE9",
    dark_hover_bg = "#81A1C1",
    dark_color = "#2E3440"
  ),
  adminlte_global(
    content_bg = "#aaaaaa"
  )
)

# create tribble for box global config
box_config <- tibble::tribble(
  ~background, ~labelStatus,
  "red", "warning",
  "purple", "success",
  "green", "primary",
  "yellow", "danger",
  "fuchsia", "info"
)

# box factory function
box_factory <- function(background, labelStatus) {
  box(
    title = "Cyberpunk Box", 
    collapsible = TRUE, 
    background = background,
    height = "200px",
    label = boxLabel(1, labelStatus)
  )
}

# pmap magic
boxes <- purrr::pmap(box_config, box_factory)

shinyApp(
   ui = dashboardPage(
     freshTheme = theme,
     skin = "blue",
     options = list(sidebarExpandOnHover = TRUE),
     header = dashboardHeader(
       dropdownMenu(
         type = "messages", 
         badgeStatus = "success",
         messageItem(
           from = "Support Team",
           message = "This is the content of a message.",
           time = "5 mins"
         ),
         messageItem(
           from = "Support Team",
           message = "This is the content of another message.",
           time = "2 hours"
         )
       )
     ),
     sidebar = dashboardSidebar(
       sidebarMenu(
         menuItem("Item 1", badgeLabel = icon("heart"), badgeColor = "light-blue"),
         menuItem("Item 2", badgeLabel = icon("poo"), badgeColor = "maroon")
       )
     ),
     body = dashboardBody(boxes),
     controlbar = dashboardControlbar(),
     title = "Fresh theming"
   ),
   server = function(input, output) { }
 )
```
