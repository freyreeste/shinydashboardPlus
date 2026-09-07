# AdminLTE2 skin selector

skinSelector creates a skin selector element.

skinSelectorItem creates an item to insert in a skin selector object.
Used internally by skinSelector.

## Usage

``` r
skinSelector()

skinSelectorItem(color)
```

## Arguments

- color:

  Skin color: "blue", "black", "purple", "red", "green", "yellow" as
  well as "blue-light", "black-light", "purple-light", "red-light",
  "green-light" and "yellow-light".

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
     body = dashboardBody(),
     controlbar = dashboardControlbar(skinSelector()),
     title = "Skin Selector"
   ),
   server = function(input, output) { }
 )
}
```
