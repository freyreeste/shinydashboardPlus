# Enhanced Header Elements

## Left Navbar Elements

By default with
[shinydashboard](https://rstudio.github.io/shinydashboard/), all
elements included in the navbar will be displayed on the right side.
[shinydashboardPlus](https://github.com/RinteRface/shinydashboardPlus)
has a new option to add elements in the left part of the
[`dashboardHeader()`](../reference/dashboardHeader.md). Such items must
be passed in the *leftUi* argument (if multiple elements, they must be
wrapped in a
[`tagList()`](https://rstudio.github.io/htmltools/reference/tagList.html),
as shown below).

``` r

library(shiny)
library(shinyWidgets)
library(shinydashboard)
library(shinydashboardPlus)
 shinyApp(
   ui = dashboardPage(
     header = dashboardHeader(
       leftUi = tagList(
         dropdownButton(
           label = "Controls",
           icon = icon("sliders-h"),
           status = "primary",
           circle = FALSE,
           sliderInput(
             inputId = "n",
             label = "Number of observations",
             min = 10, max = 100, value = 30
           ),
           prettyToggle(
             inputId = "na",
             label_on = "NAs kept",
             label_off = "NAs removed",
             icon_on = icon("check"),
             icon_off = icon("trash")
           )
         ),
         dropdownMenu(
           type = "messages", 
           badgeStatus = "success",
           messageItem(from = "Support Team", message = "This is the content of a message.", time = "5 mins"),
           messageItem(from = "Support Team", message = "This is the content of another message.", time = "2 hours"),
           messageItem(from = "New User", message = "Can I get some help?", time = "Today")
         )
       )
     ),
     sidebar = dashboardSidebar(),
     body = dashboardBody(
       setShadow(class = "dropdown-menu")
     ),
     title = "DashboardPage"
   ),
   server = function(input, output) { }
 )
```

This new feature perfectly works with the
[`dropdownButton()`](https://dreamrs.github.io/shinyWidgets/reference/dropdownButton.html)
from the [shinyWidgets](https://github.com/dreamRs/shinyWidgets)
packages by [dreamRs](https://twitter.com/_pvictorr) (as long as the
screen size is large enough), as well as the classic
[`dropdownMenu()`](https://rdrr.io/pkg/shinydashboard/man/dropdownMenu.html)
from [shinydashboard](https://rstudio.github.io/shinydashboard/). With
other individual elements, the result may not be as good, mainly for a
space reason. Indeed, a
[`sliderInput()`](https://rdrr.io/pkg/shiny/man/sliderInput.html) would
not be optimized to be embedded in the header since its label which
takes too much space. This would require some CSS tricks, namely,
reducing the slider size, and this is not the philosophy of
[shinydashboardPlus](https://github.com/RinteRface/shinydashboardPlus).

## Improved `dropdownMenu()`

The new function [`dropdownBlock()`](../reference/dropdownBlock.md) make
it easy to embed input elements in a left navbar menu. It does not hide
when the user click inside and is optimized to correctly render on
mobile devices (contrary to
[`dropdownButton()`](https://dreamrs.github.io/shinyWidgets/reference/dropdownButton.html),
see above).

``` r

shinyApp(
  ui = dashboardPage(
    header = dashboardHeader(
      leftUi = tagList(
        dropdownBlock(
          id = "mydropdown",
          title = "Dropdown 1",
          icon = "sliders-h",
          sliderInput(
            inputId = "n",
            label = "Number of observations",
            min = 10, max = 100, value = 30
          ),
          prettyToggle(
            inputId = "na",
            label_on = "NAs kept",
            label_off = "NAs removed",
            icon_on = icon("check"),
            icon_off = icon("trash")
          )
        ),
        dropdownBlock(
          id = "mydropdown2",
          title = "Dropdown 2",
          icon = "sliders-h",
          prettySwitch(
            inputId = "switch4",
            label = "Fill switch with status:",
            fill = TRUE, 
            status = "primary"
          ),
          prettyCheckboxGroup(
            inputId = "checkgroup2",
            label = "Click me!", 
            thick = TRUE,
            choices = c("Click me !", "Me !", "Or me !"),
            animation = "pulse", 
            status = "info"
          )
        )
      )
    ),
    sidebar = dashboardSidebar(),
    body = dashboardBody(
      setShadow(class = "dropdown-menu")
    ),
    title = "DashboardPage"
  ),
  server = function(input, output) { }
)
```

## Other navbar items

### Enhanced dropdownMenu Items

In
[shinydashboardPlus](https://github.com/RinteRface/shinydashboardPlus),
[`taskItem()`](../reference/taskItem.md),
[`messageItem()`](../reference/messageItem.md) and `notificationItem`
have a new *inputId* parameter allowing them to behave like
[`shiny::actionButton`](https://rdrr.io/pkg/shiny/man/actionButton.html).
This has always been quite frustrating not to be able to interact more
with these elements in
[shinydashboard](https://rstudio.github.io/shinydashboard/).

### dashboardUser Component

In the same spirit of the
[`sidebarUserPanel()`](https://rdrr.io/pkg/shinydashboard/man/sidebarUserPanel.html)
that display user informations on the sidebar, the brand new
[`dashboardUser()`](../reference/dashboardUser.md) dropdown component
may be used as an admin panel or to display further information.
[`dashboardUserItem()`](../reference/dashboardUserItem.md) provides a
refined column container.

Expand

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdib3g9IjAgMCAyNCAyNCIgc3R5bGU9ImhlaWdodDoxZW07d2lkdGg6MWVtO2ZpbGw6Y3VycmVudENvbG9yOyIgYXJpYS1oaWRkZW49InRydWUiIHJvbGU9ImltZyI+PHBhdGggZD0iTTIwIDVDMjAgNC40IDE5LjYgNCAxOSA0SDEzQzEyLjQgNCAxMiAzLjYgMTIgM0MxMiAyLjQgMTIuNCAyIDEzIDJIMjFDMjEuNiAyIDIyIDIuNCAyMiAzVjExQzIyIDExLjYgMjEuNiAxMiAyMSAxMkMyMC40IDEyIDIwIDExLjYgMjAgMTFWNVpNNCAxOUM0IDE5LjYgNC40IDIwIDUgMjBIMTFDMTEuNiAyMCAxMiAyMC40IDEyIDIxQzEyIDIxLjYgMTEuNiAyMiAxMSAyMkgzQzIuNCAyMiAyIDIxLjYgMiAyMVYxM0MyIDEyLjQgMi40IDEyIDMgMTJDMy42IDEyIDQgMTIuNCA0IDEzVjE5WiIgLz48L3N2Zz4=)

[Code](#dashboard-user)

``` r

library(shiny)
library(shinydashboard)
library(shinydashboardPlus)

shinyApp(
  ui = dashboardPage(
    header = dashboardHeader(userOutput("user")),
    sidebar = dashboardSidebar(),
    body = dashboardBody(),
    title = "User dropdown"
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
```
