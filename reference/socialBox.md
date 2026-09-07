# AdminLTE2 social box

socialBox creates a special box dedicated for social content.

userBlock goes in the title of socialBox.

boxComment has to be inserted in the comment slot of socialBox.

## Usage

``` r
socialBox(
  ...,
  title = NULL,
  footer = NULL,
  width = 6,
  height = NULL,
  collapsible = TRUE,
  collapsed = FALSE,
  closable = FALSE,
  boxToolSize = "sm",
  headerBorder = TRUE,
  label = NULL,
  dropdownMenu = NULL,
  sidebar = NULL,
  id = NULL
)

userBlock(image, title, subtitle = NULL, href = "javascript:void(0)")

boxComment(..., image, title = NULL, date = NULL)
```

## Arguments

- ...:

  comment content.

- title:

  comment title.

- footer:

  Optional footer text.

- width:

  The width of the box, using the Bootstrap grid system. This is used
  for row-based layouts. The overall width of a region is 12, so the
  default valueBox width of 4 occupies 1/3 of that width. For
  column-based layouts, use `NULL` for the width; the width is set by
  the column that contains the box.

- height:

  The height of a box, in pixels or other CSS unit. By default the
  height scales automatically with the content.

- collapsible:

  If TRUE, display a button in the upper right that allows the user to
  collapse the box.

- collapsed:

  If TRUE, start collapsed. This must be used with `collapsible=TRUE`.

- closable:

  If TRUE, display a button in the upper right that allows the user to
  close the box.

- boxToolSize:

  Size of the toolbox: choose among "xs", "sm", "md", "lg".

- headerBorder:

  Whether to display a border between the header and body. TRUE by
  default.

- label:

  Slot for [boxLabel](boxLabel.md).

- dropdownMenu:

  List of items in the boxtool dropdown menu. Use [boxDropdown](box.md).

- sidebar:

  Slot for [boxSidebar](boxSidebar.md).

- id:

  If passed, the item will behave like an action button.

- image:

  author image, if any.

- subtitle:

  Any subtitle.

- href:

  Target url or page.

- date:

  date of publication.

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
        socialBox(
          title = userBlock(
            image = "https://adminlte.io/themes/AdminLTE/dist/img/user4-128x128.jpg",
            title = "Social Box",
            subtitle = "example-01.05.2018"
          ),
          "Some text here!",
          attachmentBlock(
            image = "https://adminlte.io/themes/AdminLTE/dist/img/photo1.png",
            title = "Test",
            href = "https://google.com",
            "This is the content"
          ),
          lapply(X = 1:10, FUN = function(i) {
            boxComment(
              image = "https://adminlte.io/themes/AdminLTE/dist/img/user3-128x128.jpg",
              title = paste("Comment", i),
              date = "01.05.2018",
              paste0("The ", i, "-th comment")
            )
          }),
          footer = "The footer here!"
        )
      ),
      controlbar = dashboardControlbar(),
      title = "socialBox"
    ),
    server = function(input, output) { }
  )
}
```
