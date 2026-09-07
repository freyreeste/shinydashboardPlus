# AdminLTE2 product list container

productList creates a container to display commercial items in an
elegant container. Insert in a [box](box.md).

productListItem creates a product item to insert in productList.

## Usage

``` r
productList(...)

productListItem(..., image = NULL, title = NULL, subtitle = NULL, color = NULL)
```

## Arguments

- ...:

  product description.

- image:

  image url, if any.

- title:

  product name.

- subtitle:

  product price.

- color:

  price color: see here for a list of valid colors
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

## Author

David Granjon, <dgranjon@ymail.com>

## Examples

``` r

# Box with productList
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
          title = "Product List",
          status = "primary",
          productList(
            productListItem(
              image = "https://www.pngmart.com/files/1/Haier-TV-PNG.png",
              title = "Samsung TV",
              subtitle = "$1800",
              color = "yellow",
              "This is an amazing TV, but I don't like TV!"
            ),
            productListItem(
              image = "https://upload.wikimedia.org/wikipedia/commons/7/77/IMac_Pro.svg",
              title = "Imac 27",
              subtitle = "$4999",
              color = "red",
              "This is were I spend most of my time!"
            )
          )
        )
      ),
      title = "Product List"
    ),
    server = function(input, output) { }
  )
}
```
