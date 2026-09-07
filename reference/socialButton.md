# AdminLTE2 social button

Create a social button

## Usage

``` r
socialButton(href, icon)
```

## Arguments

- href:

  External link.

- icon:

  social network icon: see here for valid names
  <https://adminlte.io/themes/AdminLTE/pages/UI/buttons.html>.

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
          title = "Social Buttons",
          status = NULL,
          socialButton(
            href = "https://dropbox.com",
            icon = icon("dropbox")
          ),
          socialButton(
            href = "https://github.com",
            icon = icon("github")
          )
        )
      ),
      title = "Social Buttons"
    ),
    server = function(input, output) { }
  )
}
```
