# Custom messageItem

Custom messageItem

## Usage

``` r
messageItem(
  from,
  message,
  icon = shiny::icon("user"),
  time = NULL,
  href = NULL,
  inputId = NULL
)
```

## Arguments

- from:

  Who the message is from.

- message:

  Text of the message.

- icon:

  An icon tag, created by
  [`shiny::icon()`](https://rdrr.io/pkg/shiny/man/icon.html).

- time:

  String representing the time the message was sent. Any string may be
  used. For example, it could be a relative date/time like "5 minutes",
  "today", or "12:30pm yesterday", or an absolute time, like "2014-12-01
  13:45". If NULL, no time will be displayed.

- href:

  An optional URL to link to.

- inputId:

  If not NULL, this item behaves like an action button.
