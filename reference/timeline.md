# AdminLTE2 timeline block

timelineBlock creates a timeline block that may be inserted in a
[box](box.md) or outside.

timelineLabel creates a timeline label element to highlight an event.

timelineItem creates a timeline item that contains information for a
given event like the title, description, date, ...

timelineItemMedia create a specific container for images.

timelineStart indicates a starting point.

timelineEnd indicates an end point.

## Usage

``` r
timelineBlock(..., reversed = TRUE, width = 6)

timelineLabel(..., color = NULL)

timelineItem(
  ...,
  icon = NULL,
  color = NULL,
  time = NULL,
  title = NULL,
  border = TRUE,
  footer = NULL
)

timelineItemMedia(image = NULL, height = NULL, width = NULL)

timelineStart(icon = shiny::icon("clock"), color = NULL)

timelineEnd(icon = shiny::icon("hourglass-end"), color = NULL)
```

## Arguments

- ...:

  any element.

- reversed:

  Whether the timeline is reversed or not.

- width:

  media width in pixels.

- color:

  item color: see here for a list of valid colors
  <https://adminlte.io/themes/AdminLTE/pages/UI/general.html>. See
  below:

  - `light-blue (primary status)`: \#3c8dbc .

  - `red (danger status)`: \#dd4b39 .

  - `green (success status)`: \#00a65a .

  - `aqua (info status)`: \#00c0ef .

  - `yellow (warning status)`: \#f39c12 .

  - `blue`: \#0073b7 .

  - `navy`: \#001F3F .

  - `teal`: \#39CCCC .

  - `olive`: \#3D9970 .

  - `lime`: \#01FF70 .

  - `orange`: \#FF851B .

  - `fuchsia`: \#F012BE .

  - `purple`: \#605ca8 .

  - `maroon`: \#D81B60 .

  - `black`: \#111 .

  - `gray`: \#d2d6de .

- icon:

  item icon. Expect [`icon`](https://rdrr.io/pkg/shiny/man/icon.html).

- time:

  item date or time.

- title:

  item title.

- border:

  Whether to display a border between the header and the body. TRUE by
  default.

- footer:

  item footer if any.

- image:

  media url or path.

- height:

  media height in pixels.

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
        h3("When Reversed = TRUE, can be displayed inside a box"),
        box(
          title = "Timeline",
          status = "info",
          timelineBlock(
            width = 12,
            timelineEnd(color = "red"),
            timelineLabel(2018, color = "teal"),
            timelineItem(
              title = "Item 1",
              icon = icon("gears"),
              color = "olive",
              time = "now",
              footer = "Here is the footer",
              "This is the body"
            ),
            timelineItem(
              title = "Item 2",
              border = FALSE
            ),
            timelineLabel(2015, color = "orange"),
            timelineItem(
              title = "Item 3",
              icon = icon("paint-brush"),
              color = "maroon",
              timelineItemMedia(image = "placeholders/150x150.png"),
              timelineItemMedia(image = "placeholders/150x150.png")
            ),
            timelineStart(color = "purple")
          )
        ),
        h3("When Reversed = FALSE, can be displayed out of a box"),
        timelineBlock(
          reversed = FALSE,
          timelineEnd(color = "red"),
          timelineLabel(2018, color = "teal"),
          timelineItem(
            title = "Item 1",
            icon = icon("gears"),
            color = "olive",
            time = "now",
            footer = "Here is the footer",
            "This is the body"
          ),
          timelineItem(
            title = "Item 2",
            border = FALSE
          ),
          timelineLabel(2015, color = "orange"),
          timelineItem(
            title = "Item 3",
            icon = icon("paint-brush"),
            color = "maroon",
            timelineItemMedia(image = "placeholders/150x150.png"),
            timelineItemMedia(image = "placeholders/150x150.png")
          ),
          timelineStart(color = "purple")
        )
      ),
      title = "timelineBlock"
    ),
    server = function(input, output) { }
  )
}
```
