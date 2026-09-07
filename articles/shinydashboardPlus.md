# shinydashboardPlus

## Introduction

[shinydashboardPlus](https://github.com/RinteRface/shinydashboardPlus)
relies on the same basis as
[shinydashboard](https://rstudio.github.io/shinydashboard/), that is the
AdminLTE HTML
[template](https://adminlte.io/themes/AdminLTE/index2.html). It provides
extra elements that will help you to develop Shiny apps with a more
professional look and feel. Below is a summary of the main features.

| Features (sample) | shinydashboard | shinydashboardPlus |
|----|:--:|---:|
| right sidebar (controlbar) | ❌ | ✅ |
| semi collapsible sidebar (sidebar mini) | ❌ | ✅ |
| expand on hover sidebar | ❌ | ✅ |
| closable boxes | ❌ | ✅ |
| box sidebar | ❌ | ✅ |
| get box state on the server (open, closed, …) | ❌ | ✅ |
| control sidebars on the server | ❌ | ✅ |
| dashboard user dropdown | ❌ | ✅ |
| theme selector | ❌ | ✅ |
| social box | ❌ | ✅ |
| user box | ❌ | ✅ |
| control AdminLTE options | ❌ | ✅ |
| seamlessly customize appearance | ❌ | ✅ |
| beautiful preloaders | ❌ | ✅ |
| scroll to top button! | ❌ | ✅ |

Since the 2.0.0 release,
[shinydashboardPlus](https://github.com/RinteRface/shinydashboardPlus)
overwrites most of the
[shinydashboard](https://rstudio.github.io/shinydashboard/) functions
such as [`dashboardPage()`](../reference/dashboardPage.md) and
[`box()`](../reference/box.md) to facilitate the transition from one
package to another.

## What changes in v2.0.0 ?

### Breaking changes

v2.0.0 is clearly a **major breaking change** for
[shinydashboardPlus](https://github.com/RinteRface/shinydashboardPlus).
It means that coming from v0.7.5 (latest CRAN version to date), you will
have to rewrite most of the code. It was not an easy decision to take
but necessary to improve the package quality (naming consistency, …).
Now the transition from
[shinydashboard](https://rstudio.github.io/shinydashboard/) to
[shinydashboardPlus](https://github.com/RinteRface/shinydashboardPlus)
will be easier since function parameters have been harmonized. The old
`rightSidebar()` component becomes the
[`dashboardControlbar()`](../reference/controlbar.md) to ease the
transition from
[shinydashboardPlus](https://github.com/RinteRface/shinydashboardPlus)
to [bs4Dash](https://github.com/RinteRface/bs4Dash), the latter being
the Bootstrap 4 [version](https://github.com/RinteRface/bs4Dash) with a
more modern look and feel.

### More checks

Under the hood, functions are safer and more controls are done on the
user inputs to reduce the risk of accidentally providing wrong values.

### New features

The most exiting features of 2.0.0 are probably the ability to leverage
the awesome [fresh](https://github.com/dreamRs/fresh) package (see
[here](https://dreamrs.github.io/fresh/articles/vars-shinydashboard.html)
for more details) through the
[`dashboardPage()`](../reference/dashboardPage.md) *freshTheme*
parameter. Additionally, the
[`skinSelector()`](../reference/skinSelector.md) allows to dynamically
change the dashboard skin on the client side. There are also more
`update_` functions to programmatically control elements from the
server. Now the [`dashboardSidebar()`](../reference/sidebar.md) may be
collapsed, so it the
[`dashboardControlbar()`](../reference/controlbar.md). The
[`dashboardPage()`](../reference/dashboardPage.md) *options* parameter
is an easy way to fine tune the AdminLTE behavior (see
[here](https://adminlte.io/themes/AdminLTE/documentation/index.html#adminlte-options)
for the list of available options). The [`box()`](../reference/box.md)
component has been reworked to reduce the number of parameters and
include new sub-components like the
[`boxSidebar()`](../reference/boxSidebar.md) that may be
programmatically collapsed, or the
[`boxLabel()`](../reference/boxLabel.md). [`box()`](../reference/box.md)
has an input binding indicating its current state on the server side, to
perform specific tasks. Finally, colors are better documented thanks to
Victor Perrier from dreamRs. For instance, the primary color is shown as
, danger is , which eventually helps users to choose between all
available options.

## Basic Example

Below is a simple app you may build with
[shinydashboardPlus](https://github.com/RinteRface/shinydashboardPlus).
We explicitly configured the sidebar to expand on hover, through the
options parameters. Interestingly, you’ll be able to notice the scroll
to top button feature if you scroll to the bottom (bottom-right corner).

Expand

![](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdib3g9IjAgMCAyNCAyNCIgc3R5bGU9ImhlaWdodDoxZW07d2lkdGg6MWVtO2ZpbGw6Y3VycmVudENvbG9yOyIgYXJpYS1oaWRkZW49InRydWUiIHJvbGU9ImltZyI+PHBhdGggZD0iTTIwIDVDMjAgNC40IDE5LjYgNCAxOSA0SDEzQzEyLjQgNCAxMiAzLjYgMTIgM0MxMiAyLjQgMTIuNCAyIDEzIDJIMjFDMjEuNiAyIDIyIDIuNCAyMiAzVjExQzIyIDExLjYgMjEuNiAxMiAyMSAxMkMyMC40IDEyIDIwIDExLjYgMjAgMTFWNVpNNCAxOUM0IDE5LjYgNC40IDIwIDUgMjBIMTFDMTEuNiAyMCAxMiAyMC40IDEyIDIxQzEyIDIxLjYgMTEuNiAyMiAxMSAyMkgzQzIuNCAyMiAyIDIxLjYgMiAyMVYxM0MyIDEyLjQgMi40IDEyIDMgMTJDMy42IDEyIDQgMTIuNCA0IDEzVjE5WiIgLz48L3N2Zz4=)

[Code](#basic-demo)

``` r

library(shiny)
library(shinydashboard)
library(shinydashboardPlus)
shinyApp(
   ui = dashboardPage(
     options = list(sidebarExpandOnHover = TRUE),
     header = dashboardHeader(),
     sidebar = dashboardSidebar(minified = TRUE, collapsed = TRUE),
     body = dashboardBody(
      lapply(1:20, box, width = 12, title = "box")
     ),
     controlbar = dashboardControlbar(),
     title = "DashboardPage"
   ),
   server = function(input, output) { }
 )
```
