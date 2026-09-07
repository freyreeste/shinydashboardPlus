# Create a dashboard user profile.

Create a dashboard user profile.

## Usage

``` r
dashboardUser(
  ...,
  name = NULL,
  image = NULL,
  title = NULL,
  subtitle = NULL,
  footer = NULL
)
```

## Arguments

- ...:

  Body content. Slot for [dashboardUserItem](dashboardUserItem.md).

- name:

  User name.

- image:

  User profile picture.

- title:

  A title.

- subtitle:

  A subtitle.

- footer:

  Footer is any.

## See also

[`userOutput`](userOutput.md) and [`renderUser`](renderUser.md) for
dynamically-generating `dashboardUser`.

## Examples

``` r
if (interactive()) {
  library(shiny)
  library(shinyWidgets)
  library(shinydashboard)
  library(shinydashboardPlus)

  shinyApp(
    ui = dashboardPage(
      header = dashboardHeader(userOutput("user")),
      sidebar = dashboardSidebar(),
      body = dashboardBody(),
      title = "DashboardPage"
    ),
    server = function(input, output) {
      output$user <- renderUser({
        dashboardUser(
          name = "Divad Nojnarg",
          image = "https://adminlte.io/themes/AdminLTE/dist/img/user2-160x160.jpg",
          title = "shinydashboardPlus",
          subtitle = "Author",
          footer = p("The footer", class = "text-center"),
          fluidRow(
            dashboardUserItem(
              width = 6,
              socialButton(
                href = "https://dropbox.com",
                icon = icon("dropbox")
              )
            ),
            dashboardUserItem(
              width = 6,
              socialButton(
                href = "https://github.com",
                icon = icon("github")
              )
            )
          )
        )
      })
    }
  )
}
```
