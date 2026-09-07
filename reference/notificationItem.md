# Custom notificationItem

Custom notificationItem

## Usage

``` r
notificationItem(
  text,
  icon = shiny::icon("triangle-exclamation"),
  status = "success",
  href = NULL,
  inputId = NULL
)
```

## Arguments

- text:

  The notification text.

- icon:

  An icon tag, created by
  [`shiny::icon()`](https://rdrr.io/pkg/shiny/man/icon.html).

- status:

  The status of the item This determines the item's background color.
  Valid statuses are listed in
  [validStatuses](https://rdrr.io/pkg/shinydashboard/man/validStatuses.html).

- href:

  An optional URL to link to.

- inputId:

  If not NULL, this item behaves like an action button.
