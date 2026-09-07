# AdminLTE2 carousel container

carousel creates a carousel container to display media content.

carouselItem creates a carousel item to insert in a carousel.

## Usage

``` r
carousel(..., id, indicators = TRUE, width = 6, .list = NULL)

carouselItem(..., caption = NULL, active = FALSE)
```

## Arguments

- ...:

  Element such as images, iframe, ...

- id:

  Carousel id. Must be unique.

- indicators:

  Whether to display left and right indicators.

- width:

  Carousel width. 6 by default.

- .list:

  Should you need to pass carouselItem via
  [lapply](https://rdrr.io/r/base/lapply.html) or similar, put these
  item here instead of passing them in ...

- caption:

  Item caption.

- active:

  Whether the item is active or not at start.

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
      body = dashboardBody(
        carousel(
          id = "mycarousel",
          carouselItem(
            caption = "Item 1",
            tags$img(src = "https://placehold.it/900x500/3c8dbc/ffffff&text=I+Love+Bootstrap")
          ),
          carouselItem(
            caption = "Item 2",
            tags$img(src = "https://placehold.it/900x500/39CCCC/ffffff&text=I+Love+Bootstrap")
          )
        )
      ),
      title = "Carousel"
    ),
    server = function(input, output) { }
  )
}
```
