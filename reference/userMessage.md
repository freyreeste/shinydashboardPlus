# AdminLTE2 user message container

userMessages creates a user message container. Maybe inserted in a
[box](box.md).

userMessage creates a user message html element.

updateUserMessages allows to interact with a userMessages container,
such as sending, removing or editing messages.

## Usage

``` r
userMessages(..., id = NULL, status, width = 4, height = NULL)

userMessage(
  ...,
  author,
  date = NULL,
  image = NULL,
  type = c("sent", "received")
)

updateUserMessages(
  id,
  action = c("add", "remove", "update"),
  index = NULL,
  content = NULL,
  session = shiny::getDefaultReactiveDomain()
)
```

## Arguments

- ...:

  Message text.

- id:

  userMessages to target.

- status:

  Messages status. See here for a list of valid colors
  <https://adminlte.io/themes/AdminLTE/pages/UI/general.html>. Valid
  statuses are defined as follows:

  - `primary`: \#3c8dbc

  - `success`: \#00a65a

  - `info`: \#00c0ef

  - `warning`: \#f39c12

  - `danger`: \#f56954

- width:

  Container width: between 1 and 12.

- height:

  Container height.

- author:

  Message author.

- date:

  Message date.

- image:

  Message author image path or url.

- type:

  Message type: `c("sent", "received")`.

- action:

  Action to perform: add, remove or update.

- index:

  Index of item to update or remove.

- content:

  New message content in a list. For actions like add and update only!
  See example.

- session:

  Shiny session object.

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
          title = "Box with messages",
          solidHeader = TRUE,
          status = "warning",
          userMessages(
            width = 12,
            status = "success",
            userMessage(
              author = "Alexander Pierce",
              date = "20 Jan 2:00 pm",
              image = "https://adminlte.io/themes/AdminLTE/dist/img/user1-128x128.jpg",
              type = "sent",
              "Is this template really for free? That's unbelievable!"
            ),
            userMessage(
              author = "Sarah Bullock",
              date = "23 Jan 2:05 pm",
              image = "https://adminlte.io/themes/AdminLTE/dist/img/user3-128x128.jpg",
              type = "received",
              "You better believe it!"
            )
          )
        ),
        userMessages(
          width = 6,
          status = "danger",
          userMessage(
            author = "Alexander Pierce",
            date = "20 Jan 2:00 pm",
            image = "https://adminlte.io/themes/AdminLTE/dist/img/user1-128x128.jpg",
            type = "received",
            "Is this template really for free? That's unbelievable!"
          ),
          userMessage(
            author = "Sarah Bullock",
            date = "23 Jan 2:05 pm",
            image = "https://adminlte.io/themes/AdminLTE/dist/img/user3-128x128.jpg",
            type = "sent",
            "You better believe it!"
          )
        )
      ),
      title = "user Message"
    ),
    server = function(input, output) { }
  )
}

if (interactive()) {
  library(shiny)
  library(shinydashboard)
  library(shinydashboardPlus)

  shinyApp(
    ui = dashboardPage(
      dashboardHeader(),
      dashboardSidebar(),
      dashboardBody(
        fluidRow(
          actionButton("remove", "Remove message"),
          actionButton("add", "Add message"),
          actionButton("update", "Update message")
        ),
        numericInput("index", "Message index:", 1, min = 1, max = 3),
        br(),
        br(),
        userMessages(
          width = 6,
          status = "danger",
          id = "message",
          userMessage(
            author = "Alexander Pierce",
            date = "20 Jan 2:00 pm",
            image = "https://adminlte.io/themes/AdminLTE/dist/img/user1-128x128.jpg",
            type = "received",
            "Is this template really for free? That's unbelievable!"
          ),
          userMessage(
            author = "Sarah Bullock",
            date = "23 Jan 2:05 pm",
            image = "https://adminlte.io/themes/AdminLTE/dist/img/user3-128x128.jpg",
            type = "sent",
            "You better believe it!"
          )
        )
      ),
      title = "user Message"
    ),
    server = function(input, output, session) {
      observeEvent(input$remove, {
        updateUserMessages("message", action = "remove", index = input$index)
      })
      observeEvent(input$add, {
        updateUserMessages(
          "message",
          action = "add",
          content = list(
            author = "David",
            date = "Now",
            image = "https://i.pinimg.com/originals/f1/15/df/f115dfc9cab063597b1221d015996b39.jpg",
            type = "received",
            text = tagList(
              sliderInput(
                "obs",
                "Number of observations:",
                min = 0,
                max = 1000,
                value = 500
              ),
              plotOutput("distPlot")
            )
          )
        )
      })

      output$distPlot <- renderPlot({
        hist(rnorm(input$obs))
      })

      observeEvent(input$update, {
        updateUserMessages(
          "message",
          action = "update",
          index = input$index,
          content = list(
            text = tagList(
              appButton(
                inputId = "reload",
                label = "Click me!",
                icon = icon("arrows-rotate"),
                dashboardBadge(1, color = "orange")
              )
            )
          )
        )
      })

      observeEvent(input$reload, {
        showNotification("Yeah!", duration = 1, type = "default")
      })
    }
  )
}
```
