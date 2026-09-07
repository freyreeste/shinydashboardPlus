# Create a box for the main body of a dashboard

box can be used to hold content in the main body of a dashboard.

updateBox is used to toggle, close or restore a box on the client.

boxDropdown is used in the dropdown parameter of box.

boxDropdownItem goes in boxDropdown.

dropdownDivider goes in boxDropdown but also in any dropdown menu
container.

boxPad creates a vertical container for descriptionBlock. It has to be
included in a box.

descriptionBlock creates a description block, perfect for writing
statistics to insert in a box

## Usage

``` r
box(
  ...,
  title = NULL,
  footer = NULL,
  status = NULL,
  solidHeader = FALSE,
  background = NULL,
  width = 6,
  height = NULL,
  collapsible = FALSE,
  collapsed = FALSE,
  closable = FALSE,
  icon = NULL,
  gradient = FALSE,
  boxToolSize = "sm",
  headerBorder = TRUE,
  label = NULL,
  dropdownMenu = NULL,
  sidebar = NULL,
  id = NULL
)

updateBox(
  id,
  action = c("remove", "toggle", "restore", "update"),
  options = NULL,
  session = shiny::getDefaultReactiveDomain()
)

boxDropdown(..., icon = shiny::icon("wrench"))

boxDropdownItem(..., id = NULL, href = NULL, icon = NULL)

dropdownDivider()

boxPad(..., color = NULL, style = NULL)

descriptionBlock(
  number = NULL,
  numberColor = NULL,
  numberIcon = NULL,
  header = NULL,
  text = NULL,
  rightBorder = TRUE,
  marginBottom = FALSE
)
```

## Arguments

- ...:

  any element such as descriptionBlock.

- title:

  Optional title.

- footer:

  Optional footer text.

- status:

  The status of the item This determines the item's background color.
  Valid statuses are defined as follows:

  - `primary`: \#3c8dbc

  - `success`: \#00a65a

  - `info`: \#00c0ef

  - `warning`: \#f39c12

  - `danger`: \#f56954

  - `navy`: \#001F3F

  - `teal`: \#39CCCC

  - `purple`: \#605ca8

  - `orange`: \#ff851b

  - `maroon`: \#D81B60

  - `black`: \#111111

  Only primary, success, info, warning and danger are compatible with
  solidHeader!

- solidHeader:

  Should the header be shown with a solid color background?

- background:

  If NULL (the default), the background of the box will be white.
  Otherwise, a color string. Valid colors are listed in
  [validColors](validColors.md). See below:

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

- width:

  The width of the box, using the Bootstrap grid system. This is used
  for row-based layouts. The overall width of a region is 12, so the
  default valueBox width of 4 occupies 1/3 of that width. For
  column-based layouts, use `NULL` for the width; the width is set by
  the column that contains the box.

- height:

  The height of a box, in pixels or other CSS unit. By default the
  height scales automatically with the content.

- collapsible:

  If TRUE, display a button in the upper right that allows the user to
  collapse the box.

- collapsed:

  If TRUE, start collapsed. This must be used with `collapsible=TRUE`.

- closable:

  If TRUE, display a button in the upper right that allows the user to
  close the box.

- icon:

  Optional icon. Expect [icon](https://rdrr.io/pkg/shiny/man/icon.html).

- gradient:

  Whether to allow gradient effect for the background color. Default to
  FALSE.

- boxToolSize:

  Size of the toolbox: choose among "xs", "sm", "md", "lg".

- headerBorder:

  Whether to display a border between the header and body. TRUE by
  default.

- label:

  Slot for [boxLabel](boxLabel.md).

- dropdownMenu:

  List of items in the boxtool dropdown menu. Use boxDropdown.

- sidebar:

  Slot for [boxSidebar](boxSidebar.md).

- id:

  If passed, the item will behave like an action button.

- action:

  Action to trigger: either collapse, remove, restore or update.

- options:

  If action is update, a list of new options to configure the box, such
  as
  `list(title = "new title", status = NULL, solidHeader = FALSE, background = "red", width = 6, height = "200px", collapsible = FALSE, closable = FALSE)`.
  If the box had a background/status (any item that may be NULL), you
  must explicitly pass background = NULL, if you want to remove the
  background value.

- session:

  Shiny session object.

- href:

  Target url or page.

- color:

  background color: see here for a list of valid colors
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

- style:

  custom CSS, if any.

- number:

  any number.

- numberColor:

  number color: see here for a list of valid colors
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

- numberIcon:

  number icon, if any. Expect
  [`icon`](https://rdrr.io/pkg/shiny/man/icon.html).

- header:

  bold text.

- text:

  additional text.

- rightBorder:

  TRUE by default. Whether to display a right border to separate two
  blocks. The last block on the right should not have a right border.

- marginBottom:

  FALSE by default. Set it to TRUE when the descriptionBlock is used in
  a boxPad context.

## Examples

``` r

# A box with label, sidebar, dropdown menu
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
        title = "Closable Box with dropdown", 
        closable = TRUE, 
        width = 12,
        status = "warning", 
        solidHeader = FALSE, 
        collapsible = TRUE,
        label = boxLabel(
         text = 1,
         status = "danger",
         style = "circle"
        ),
        dropdownMenu = boxDropdown(
         boxDropdownItem("Link to google", href = "https://www.google.com"),
         boxDropdownItem("item 2", href = "#"),
         dropdownDivider(),
         boxDropdownItem("item 3", href = "#", icon = icon("table-cells"))
        ),
        sidebar = boxSidebar(
         startOpen = TRUE,
         id = "mycardsidebar",
         sliderInput(
          "obs", 
          "Number of observations:",
          min = 0, 
          max = 1000, 
          value = 500
         )
        ),
        plotOutput("distPlot")
       )
     )
   ),
   server = function(input, output) {
    output$distPlot <- renderPlot({
     hist(rnorm(input$obs))
    })
   }
 )
}

# Toggle a box on the client
if (interactive()) {
 library(shiny)
 library(shinydashboard)
 library(shinydashboardPlus)
 
 ui <- dashboardPage(
   dashboardHeader(),
   dashboardSidebar(),
   dashboardBody(
     tags$style("body { background-color: ghostwhite}"),
     fluidRow(
       actionButton("toggle_box", "Toggle Box"),
       actionButton("remove_box", "Remove Box", class = "bg-danger"),
       actionButton("restore_box", "Restore Box", class = "bg-success")
     ),
     actionButton("update_box", "Update Box", class = "bg-info"), 
     actionButton("update_box2", "Update Box 2", class = "bg-info"),
     br(),
     br(),
     box(
       title = textOutput("box_state"),
       id = "mybox",
       status = "danger", 
       background = "maroon", 
       gradient = TRUE,
       collapsible = TRUE,
       closable = TRUE,
       plotOutput("plot")
     )
   )
 )
 
 server <- function(input, output, session) {
   output$plot <- renderPlot({
     req(!input$mybox$collapsed)
     plot(rnorm(200))
   })
   
   output$box_state <- renderText({
     state <- if (input$mybox$collapsed) "collapsed" else "uncollapsed"
     paste("My box is", state)
   })
   
   observeEvent(input$toggle_box, {
     updateBox("mybox", action = "toggle")
   })
   
   observeEvent(input$remove_box, {
     updateBox("mybox", action = "remove")
   })
   
   observeEvent(input$restore_box, {
     updateBox("mybox", action = "restore")
   })
   
   observeEvent(input$mybox$visible, {
     collapsed <- if (input$mybox$collapsed) "collapsed" else "uncollapsed"
     visible <- if (input$mybox$visible) "visible" else "hidden"
     message <- paste("My box is", collapsed, "and", visible)
     showNotification(message, type = "warning", duration = 1)
   })
   
   observeEvent(input$update_box, {
     updateBox(
       "mybox", 
       action = "update", 
       options = list(
         title = h2("hello", dashboardLabel(1, status = "primary")),
         status = "warning", 
         solidHeader = TRUE, 
         width = 12, 
         background = NULL, 
         height = "900px", 
         closable = FALSE
       )
     )
   })
    
    observeEvent(input$update_box2, {
      updateBox(
        "mybox", 
        action = "update", 
        options = list(
          status = NULL, 
          solidHeader = FALSE,
          width = 4, 
          background = "green", 
          height = "500px", 
          closable = TRUE
        )
      )
    })
   
 }
 
 shinyApp(ui, server)
}

# Box with dropdown items and input
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
         title = "Closable Box with dropdown", 
         closable = TRUE, 
         width = 12,
         status = "warning", 
         solidHeader = FALSE, 
         collapsible = TRUE,
         dropdownMenu = boxDropdown(
           boxDropdownItem("Click me", id = "dropdownItem", icon = icon("heart")),
           boxDropdownItem("item 2", href = "https://www.google.com/"),
           dropdownDivider(),
           boxDropdownItem("item 3", icon = icon("table-cells"))
         ),
         "My box"
       )
     )
   ),
   server = function(input, output) {
     observeEvent(input$dropdownItem, {
       showNotification("Hello", duration = 1, type = "message")
     })
   }
 )
}

# Box with boxPad container + descriptionBlock
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
          title = "Box with right pad",
          status = "warning",
          fluidRow(
            column(width = 6),
            column(
              width = 6,
              boxPad(
                color = "green",
                descriptionBlock(
                  header = "8390",
                  text = "VISITS",
                  rightBorder = FALSE,
                  marginBottom = TRUE
                ),
                descriptionBlock(
                  header = "30%",
                  text = "REFERRALS",
                  rightBorder = FALSE,
                  marginBottom = TRUE
                ),
                descriptionBlock(
                  header = "70%",
                  text = "ORGANIC",
                  rightBorder = FALSE,
                  marginBottom = FALSE
                )
              )
            )
          )
        )
      ),
      title = "boxPad"
    ),
    server = function(input, output) { }
  )
}


# Box with descriptionBlock
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
          solidHeader = FALSE,
          title = "Status summary",
          background = NULL,
          width = 4,
          status = "danger",
          footer = fluidRow(
            column(
              width = 6,
              descriptionBlock(
                number = "17%",
                numberColor = "green",
                numberIcon = icon("caret-up"),
                header = "$35,210.43",
                text = "TOTAL REVENUE",
                rightBorder = TRUE,
                marginBottom = FALSE
              )
            ),
            column(
              width = 6,
              descriptionBlock(
                number = "18%",
                numberColor = "red",
                numberIcon = icon("caret-down"),
                header = "1200",
                text = "GOAL COMPLETION",
                rightBorder = FALSE,
                marginBottom = FALSE
              )
            )
          )
        )
      ),
      title = "Description Blocks"
    ),
    server = function(input, output) { }
  )
}
```
