# Create a header for a dashboard page

A dashboard header can be left blank, or it can include dropdown menu
items on the right side.

## Usage

``` r
dashboardHeader(
  ...,
  title = NULL,
  titleWidth = NULL,
  disable = FALSE,
  .list = NULL,
  leftUi = NULL,
  controlbarIcon = shiny::icon("gears"),
  fixed = FALSE
)
```

## Arguments

- ...:

  Items to put in the header. Should be
  [`dropdownMenu`](https://rdrr.io/pkg/shinydashboard/man/dropdownMenu.html)s.

- title:

  An optional title to show in the header bar.. By default, this will
  also be used as the title shown in the browser's title bar. If you
  want that to be different from the text in the dashboard header bar,
  set the `title` in [`dashboardPage`](dashboardPage.md).

- titleWidth:

  The width of the title area. This must either be a number which
  specifies the width in pixels, or a string that specifies the width in
  CSS units.

- disable:

  If `TRUE`, don't display the header bar.

- .list:

  An optional list containing items to put in the header. Same as the
  `...` arguments, but in list format. This can be useful when working
  with programmatically generated items.

- leftUi:

  Items that will appear on the left part of the navbar. Should be
  wrapped in a tagList.

- controlbarIcon:

  Customize the trigger icon of the right sidebar.

- fixed:

  Whether the navbar is fixed-top or not. FALSE by default.

## Note

We do not recommend to insert shiny input elements (such as sliderInput)
in the left menu, since they will not be well displayed. Instead, wrap
them in a [`dropdownBlock`](dropdownBlock.md)

## See also

[`dropdownMenu`](https://rdrr.io/pkg/shinydashboard/man/dropdownMenu.html)

## Examples

``` r
if (interactive()) {
  library(shiny)
  library(shinyWidgets)
  library(shinydashboard)
  library(shinydashboardPlus)

  shinyApp(
    ui = dashboardPage(
      header = dashboardHeader(
        leftUi = tagList(
          dropdownBlock(
            id = "mydropdown",
            title = "Dropdown 1",
            icon = icon("sliders"),
            sliderInput(
              inputId = "n",
              label = "Number of observations",
              min = 10, max = 100, value = 30
            ),
            prettyToggle(
              inputId = "na",
              label_on = "NAs kept",
              label_off = "NAs removed",
              icon_on = icon("check"),
              icon_off = icon("trash-can")
            )
          ),
          dropdownBlock(
            id = "mydropdown2",
            title = "Dropdown 2",
            icon = icon("sliders"),
            prettySwitch(
              inputId = "switch4",
              label = "Fill switch with status:",
              fill = TRUE,
              status = "primary"
            ),
            prettyCheckboxGroup(
              inputId = "checkgroup2",
              label = "Click me!",
              thick = TRUE,
              choices = c("Click me !", "Me !", "Or me !"),
              animation = "pulse",
              status = "info"
            )
          )
        ),
        dropdownMenu(
          type = "tasks",
          badgeStatus = "danger",
          taskItem(value = 20, color = "aqua", "Refactor code"),
          taskItem(value = 40, color = "green", "Design new layout"),
          taskItem(value = 60, color = "yellow", "Another task"),
          taskItem(value = 80, color = "red", "Write documentation")
        )
      ),
      sidebar = dashboardSidebar(),
      body = dashboardBody(
        setShadow(class = "dropdown-menu")
      ),
      title = "DashboardPage"
    ),
    server = function(input, output) { }
  )
}
```
