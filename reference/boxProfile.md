# AdminLTE2 box profile

boxProfile goes inside a [box](box.md). Displays user information in an
elegant container.

boxProfileItem is an sub-element of a boxProfile.

## Usage

``` r
boxProfile(..., image = NULL, title, subtitle = NULL, bordered = FALSE)

boxProfileItem(title, description)
```

## Arguments

- ...:

  any element such as boxProfileItem.

- image:

  profile image, if any.

- title:

  item title.

- subtitle:

  subtitle.

- bordered:

  Whether the container should have a border or not. FALSE by default.

- description:

  item info.

## Author

David Granjon, <dgranjon@ymail.com>

## Examples

``` r

# Box with boxProfile
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
      title = "Box with profile",
      status = "primary",
      boxProfile(
       image = "https://adminlte.io/themes/AdminLTE/dist/img/user4-128x128.jpg",
       title = "Nina Mcintire",
       subtitle = "Software Engineer",
       bordered = TRUE,
       boxProfileItem(
        title = "Followers",
        description = 1322
       ),
       boxProfileItem(
        title = "Following",
        description = 543
       ),
       boxProfileItem(
        title = "Friends",
        description = 13287
       )
      )
     )
    ),
    title = "boxProfile"
  ),
  server = function(input, output) { }
 )
}
```
