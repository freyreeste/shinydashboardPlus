# AdminLTE2 user post

userPost creates a user post. This content may be inserted in a
[box](box.md).

userPostTagItems creates a container to host userPostTagItem.

userPostTagItem creates a user post tool item

userPostMedia creates a container to include an image in userPost.

## Usage

``` r
userPost(
  ...,
  id = NULL,
  image,
  author,
  description = NULL,
  collapsible = TRUE,
  collapsed = FALSE
)

userPostTagItems(...)

userPostTagItem(..., side = "left")

userPostMedia(image, height = NULL, width = NULL)
```

## Arguments

- ...:

  tool content such as label, button, ...

- id:

  unique id of the post.

- image:

  image path or url ...

- author:

  post author.

- description:

  post description.

- collapsible:

  If TRUE, display a button in the upper right that allows the user to
  collapse the comment.

- collapsed:

  Whether the comment is collapsed when the application starts, FALSE by
  default.

- side:

  tool item orientation: "left" of "right", "left" by default.

- height:

  media height in pixels.

- width:

  media width in pixels.

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
          title = "Box with user comment",
          status = "primary",
          userPost(
            id = 1,
            image = "https://adminlte.io/themes/AdminLTE/dist/img/user1-128x128.jpg",
            author = "Jonathan Burke Jr.",
            description = "Shared publicly - 7:30 PM today",
            "Lorem ipsum represents a long-held tradition for designers,
       typographers and the like. Some people hate it and argue for
       its demise, but others ignore the hate as they create awesome
       tools to help create filler text for everyone from bacon
       lovers to Charlie Sheen fans.",
            collapsible = FALSE,
            userPostTagItems(
              userPostTagItem(dashboardLabel("item 1", status = "info")),
              userPostTagItem(dashboardLabel("item 2", status = "danger"), side = "right")
            )
          ),
          userPost(
            id = 2,
            image = "https://adminlte.io/themes/AdminLTE/dist/img/user6-128x128.jpg",
            author = "Adam Jones",
            userPostMedia(image = "https://adminlte.io/themes/AdminLTE/dist/img/photo2.png"),
            userPostTagItems(
              userPostTagItem(dashboardLabel("item 1", status = "success")),
              userPostTagItem(dashboardLabel("item 2", status = "danger"), side = "right")
            )
          )
        )
      ),
      title = "userPost"
    ),
    server = function(input, output) { }
  )
}
```
