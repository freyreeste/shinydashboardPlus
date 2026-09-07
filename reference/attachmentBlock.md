# AdminLTE2 attachment container

attachmentBlock create an attachment container, nice to wrap articles...
and insert in a [box](box.md).

## Usage

``` r
attachmentBlock(..., image, title = NULL, href = NULL)
```

## Arguments

- ...:

  any element.

- image:

  url or path to the image.

- title:

  attachment title.

- href:

  external link.

## Author

David Granjon, <dgranjon@ymail.com>

## Examples

``` r

# Box with attachmentBlock
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
          title = "Attachment example",
          attachmentBlock(
            image = "https://adminlte.io/themes/AdminLTE/dist/img/photo1.png",
            title = "Test",
            href = "https://google.com",
            "This is the content"
          )
        )
      ),
      title = "AttachmentBlock"
    ),
    server = function(input, output) { }
  )
}
```
