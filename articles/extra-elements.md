# Extra Elements

## Accordion

Accordions are a category of collapsible elements. While collapsible
items don’t alter the state of other items in the same collapsible
container, each accordion item will toggle any other opened accordion,
to ensure that only 1 item is visible at once.
[`accordion()`](../reference/accordion.md) expects to contain
`accordionItems`. Importantly, to guaranty the uniqueness of each
accordion, we must provide an *id* parameter. This parameter allows to
programmatically toggle any accordion item, through an `updateAccordion`
function.

Expand

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdib3g9IjAgMCAyNCAyNCIgc3R5bGU9ImhlaWdodDoxZW07d2lkdGg6MWVtO2ZpbGw6Y3VycmVudENvbG9yOyIgYXJpYS1oaWRkZW49InRydWUiIHJvbGU9ImltZyI+PHBhdGggZD0iTTIwIDVDMjAgNC40IDE5LjYgNCAxOSA0SDEzQzEyLjQgNCAxMiAzLjYgMTIgM0MxMiAyLjQgMTIuNCAyIDEzIDJIMjFDMjEuNiAyIDIyIDIuNCAyMiAzVjExQzIyIDExLjYgMjEuNiAxMiAyMSAxMkMyMC40IDEyIDIwIDExLjYgMjAgMTFWNVpNNCAxOUM0IDE5LjYgNC40IDIwIDUgMjBIMTFDMTEuNiAyMCAxMiAyMC40IDEyIDIxQzEyIDIxLjYgMTEuNiAyMiAxMSAyMkgzQzIuNCAyMiAyIDIxLjYgMiAyMVYxM0MyIDEyLjQgMi40IDEyIDMgMTJDMy42IDEyIDQgMTIuNCA0IDEzVjE5WiIgLz48L3N2Zz4=)

[Code](#accordions)

``` r

library(shiny)
library(shinydashboard)
library(shinydashboardPlus)
 shinyApp(
  ui = dashboardPage(
    dashboardHeader(),
    dashboardSidebar(),
    dashboardBody(
      radioButtons("controller", "Controller", choices = c(1, 2)),
      br(),
      accordion(
       id = "accordion1",
        accordionItem(
          title = "Accordion 1 Item 1",
          status = "danger",
          collapsed = TRUE,
          "This is some text!"
        ),
        accordionItem(
          title = "Accordion 1 Item 2",
          status = "warning",
          collapsed = FALSE,
          "This is some text!"
        )
      ),
      accordion(
       id = "accordion2",
        accordionItem(
          title = "Accordion 2 Item 1",
          status = "info",
          collapsed = TRUE,
          "This is some text!"
        ),
        accordionItem(
          title = "Accordion 2 Item 2",
          status = "success",
          collapsed = FALSE,
          "This is some text!"
        )
      )
    ),
    title = "Accordion"
  ),
  server = function(input, output, session) {
    observeEvent(input$controller, {
      updateAccordion(id = "accordion1", selected = input$controller)
    })
    
    observe(print(input$accordion1))
    
    observeEvent(input$accordion1, {
      showNotification(sprintf("You selected accordion N° %s", input$accordion1), type = "message")
    })
  }
 )
```

## User messages

[shinydashboardPlus](https://github.com/RinteRface/shinydashboardPlus)
make it possible to create an entire chat system within a Shiny app.
[`userMessages()`](../reference/userMessage.md) is the main container,
[`userMessage()`](../reference/userMessage.md) being the message
element. [`updateUserMessages()`](../reference/userMessage.md) looks for
the [`userMessages()`](../reference/userMessage.md) *id* so as to:

- remove an existing message
- add a new message
- edit an existing message

Importantly, we assume that a message structure is composed as follows:

``` r
list(
  author = "David",
  date = "Now",
  image = "https://i.pinimg.com/originals/f1/15/df/f115dfc9cab063597b1221d015996b39.jpg",
  type = "received",
  text = "A new message"
```

The *type* parameter controls the message background color. For a sent
message, the color is inherited from the
[`userMessages()`](../reference/userMessage.md) status, while for a
received message, the color is gray by default. The *text* argument
refers to the message content. It may be simple text, shiny tags or
event any combinations of shiny inputs/ouput, as shown in the below
example.

Expand

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdib3g9IjAgMCAyNCAyNCIgc3R5bGU9ImhlaWdodDoxZW07d2lkdGg6MWVtO2ZpbGw6Y3VycmVudENvbG9yOyIgYXJpYS1oaWRkZW49InRydWUiIHJvbGU9ImltZyI+PHBhdGggZD0iTTIwIDVDMjAgNC40IDE5LjYgNCAxOSA0SDEzQzEyLjQgNCAxMiAzLjYgMTIgM0MxMiAyLjQgMTIuNCAyIDEzIDJIMjFDMjEuNiAyIDIyIDIuNCAyMiAzVjExQzIyIDExLjYgMjEuNiAxMiAyMSAxMkMyMC40IDEyIDIwIDExLjYgMjAgMTFWNVpNNCAxOUM0IDE5LjYgNC40IDIwIDUgMjBIMTFDMTEuNiAyMCAxMiAyMC40IDEyIDIxQzEyIDIxLjYgMTEuNiAyMiAxMSAyMkgzQzIuNCAyMiAyIDIxLjYgMiAyMVYxM0MyIDEyLjQgMi40IDEyIDMgMTJDMy42IDEyIDQgMTIuNCA0IDEzVjE5WiIgLz48L3N2Zz4=)

[Code](#user-messages)

``` r

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
          text = "A new message"
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
           icon = icon("sync"), 
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
```
