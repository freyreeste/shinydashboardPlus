# AdminLTE2 user box

userBox creates a user card.

userDescription creates a customized title tag for userBox.

## Usage

``` r
userBox(
  ...,
  title = NULL,
  footer = NULL,
  status = NULL,
  background = NULL,
  width = 6,
  height = NULL,
  collapsible = TRUE,
  collapsed = FALSE,
  closable = FALSE,
  gradient = FALSE,
  boxToolSize = "sm",
  headerBorder = TRUE,
  label = NULL,
  dropdownMenu = NULL,
  sidebar = NULL,
  id = NULL
)

userDescription(
  title,
  subtitle = NULL,
  image,
  backgroundImage = NULL,
  type = c(1, 2),
  imageElevation = NULL
)
```

## Arguments

- ...:

  any element such as [descriptionBlock](box.md).

- title:

  User card title.

- footer:

  Optional footer text.

- status:

  The status of the item This determines the item's background color.
  Valid statuses are defined as follows:

  - `primary`: \#3c8dbc

  - `success`: \#00a65a

  - `info`: \#00c0ef

  - `warning`: \#f39c12

  - `danger`: \#f56954

  - `navy`: \#001F3F

  - `teal`: \#39CCCC

  - `purple`: \#605ca8

  - `orange`: \#ff851b

  - `maroon`: \#D81B60

  - `black`: \#111111

  Only primary, success, info, warning and danger are compatible with
  solidHeader!

- background:

  If NULL (the default), the background of the box will be white.
  Otherwise, a color string. Valid colors are listed in
  [validColors](validColors.md). See below:

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

- gradient:

  Whether to allow gradient effect for the background color. Default to
  FALSE.

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

- subtitle:

  User card subtitle.

- image:

  User image url or path.

- backgroundImage:

  image url, if any. Background needs to be TRUE.

- type:

  User card type. Either 1 or 2. 1 corresponds to a centered user image,
  while 2 is a left aligned user image.

- imageElevation:

  User card image elevation (numeric). NULL by default.

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
      header = dashboardHeader(),
      sidebar = dashboardSidebar(),
      controlbar = dashboardControlbar(),
      footer = dashboardFooter(),
      title = "test",
      body = dashboardBody(
        userBox(
          title = userDescription(
            title = "Nadia Carmichael",
            subtitle = "lead Developer",
            type = 2,
            image = "https://adminlte.io/themes/AdminLTE/dist/img/user7-128x128.jpg",
          ),
          status = "primary",
          gradient = TRUE,
          background = "light-blue",
          boxToolSize = "xl",
          "Some text here!",
          footer = "The footer here!"
        ),
        userBox(
          title = userDescription(
            title = "Alexander Pierce",
            subtitle = "Founder & CEO",
            type = 1,
            image = "https://adminlte.io/themes/AdminLTE/dist/img/user1-128x128.jpg",
          ),
          status = "purple",
          closable = TRUE,
          "Some text here!",
          footer = "The footer here!"
        ),
        userBox(
          title = userDescription(
            title = "Elizabeth Pierce",
            subtitle = "Web Designer",
            image = "https://adminlte.io/themes/AdminLTE/dist/img/user3-128x128.jpg",
            backgroundImage = "https://cdn.statically.io/img/wallpaperaccess.com/full/1119564.jpg",
          ),
          status = "teal",
          closable = TRUE,
          maximizable = TRUE,
          "Some text here!",
          footer = "The footer here!"
        )
      )
    ),
    server = function(input, output) {}
  )
}
```
