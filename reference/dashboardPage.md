# Dashboard Page with a right sidebar

This creates a dashboard page for use in a Shiny app.

## Usage

``` r
dashboardPage(
  header,
  sidebar,
  body,
  controlbar = NULL,
  footer = NULL,
  title = NULL,
  skin = c("blue", "blue-light", "black", "black-light", "purple", "purple-light",
    "green", "green-light", "red", "red-light", "yellow", "yellow-light", "midnight"),
  freshTheme = NULL,
  preloader = NULL,
  md = FALSE,
  options = NULL,
  scrollToTop = FALSE
)
```

## Arguments

- header:

  A header created by [`dashboardHeader`](dashboardHeader.md).

- sidebar:

  A sidebar created by [`dashboardSidebar`](sidebar.md).

- body:

  A body created by
  [`dashboardBody`](https://rdrr.io/pkg/shinydashboard/man/dashboardBody.html).

- controlbar:

  A right sidebar created by [dashboardControlbar](controlbar.md). NULL
  by default.

- footer:

  A footer created by [dashboardFooter](dashboardFooter.md).

- title:

  A title to display in the browser's title bar. If no value is
  provided, it will try to extract the title from the
  `dashboardHeaderPlus`.

- skin:

  A color theme. See
  <https://adminlte.io/themes/AdminLTE/pages/UI/general.html>. If the
  skin is light, the sidebar will have a light background. Not
  compatible with freshTheme.

- freshTheme:

  A skin powered by the fresh package. Not compatible with skin. See
  <https://dreamrs.github.io/fresh/articles/vars-shinydashboard.html>.

- preloader:

  shinydashboardPlus uses waiter (see
  <https://waiter.john-coene.com/#/>). Pass a list like
  `list(html = spin_1(), color = "#333e48")`. `waiter` expects to
  provide a sub-list to configure
  [waiterShowOnLoad](https://rdrr.io/pkg/waiter/man/waiter.html) (refer
  to the package help for all styles). `duration` defines the loader
  timeout.

- md:

  Whether to enable material design. Experimental...

- options:

  Extra option to overwrite the vanilla AdminLTE configuration. See
  <https://adminlte.io/themes/AdminLTE/documentation/index.html#adminlte-options>.
  Expect a list.

- scrollToTop:

  Whether to display a scroll to top button whenever the page height is
  too large. Default to FALSE.

## See also

[`dashboardHeader`](dashboardHeader.md),
[`dashboardSidebar`](sidebar.md),
[`dashboardBody`](https://rdrr.io/pkg/shinydashboard/man/dashboardBody.html).

## Examples

``` r
if (interactive()) {
 library(shiny)
 library(shinydashboard)
 library(shinydashboardPlus)
 library(fresh)
 
 shinyApp(
   ui = dashboardPage(
     freshTheme = create_theme(
      adminlte_color(
        light_blue = "#55e7ff",
        blue = "#2011a2",
        navy = "#201148",
        red = "#ff34b3"
      ),
      adminlte_sidebar(
        dark_bg = "#D8DEE9",
        dark_hover_bg = "#81A1C1",
        dark_color = "#2E3440"
      ),
      adminlte_global(
        content_bg = "#FFF",
        box_bg = "#D8DEE9", 
        info_box_bg = "#D8DEE9"
      )
     ),
     options = list(sidebarExpandOnHover = TRUE),
     header = dashboardHeader(),
     sidebar = dashboardSidebar(),
     body = dashboardBody(
      box(background = "red"),
      box(background = "blue"),
      box(background = "navy")
     ),
     controlbar = dashboardControlbar(),
     title = "DashboardPage"
   ),
   server = function(input, output) { }
 )
}
```
