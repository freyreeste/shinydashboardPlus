# AdminLTE2 user list container

userList creates a user list container to be inserted in a
[box](box.md).

userListItem creates a user list item.

## Usage

``` r
userList(...)

userListItem(image, title, subtitle = NULL)
```

## Arguments

- ...:

  slot for userListItem.

- image:

  image url or path.

- title:

  Item title.

- subtitle:

  Item subtitle.

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
          title = "User List example",
          status = "success",
          userList(
            userListItem(
              image = "https://adminlte.io/themes/AdminLTE/dist/img/user1-128x128.jpg",
              title = "Shiny",
              subtitle = "Package 1"
            ),
            userListItem(
              image = "https://adminlte.io/themes/AdminLTE/dist/img/user7-128x128.jpg",
              title = "Tidyverse",
              subtitle = "Package 2"
            ),
            userListItem(
              image = "https://adminlte.io/themes/AdminLTE/dist/img/user5-128x128.jpg",
              title = "tidyr",
              subtitle = "Package 3"
            )
          )
        )
      ),
      title = "User List"
    ),
    server = function(input, output) { }
  )
}
```
