# Create a dynamic user output (client side)

This can be used as a placeholder for dynamically-generated
[`dashboardUser`](dashboardUser.md).

## Usage

``` r
userOutput(id, tag = shiny::tags$li)
```

## Arguments

- id:

  Output variable name.

- tag:

  A tag function, like `tags$li` or `tags$ul`.

## See also

[`renderUser`](renderUser.md) for the corresponding server side function
and examples.

Other user outputs: [`renderUser()`](renderUser.md)
