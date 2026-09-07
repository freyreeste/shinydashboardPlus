# Create dynamic user output (server side)

Create dynamic user output (server side)

## Usage

``` r
renderUser(expr, env = parent.frame(), quoted = FALSE, outputArgs = list())
```

## Arguments

- expr:

  An expression that returns a Shiny tag object,
  [`HTML()`](https://rstudio.github.io/htmltools/reference/HTML.html),
  or a list of such objects.

- env:

  The parent environment for the reactive expression. By default, this
  is the calling environment, the same as when defining an ordinary
  non-reactive expression. If `expr` is a quosure and `quoted` is
  `TRUE`, then `env` is ignored.

- quoted:

  If it is `TRUE`, then the
  [`quote()`](https://rdrr.io/r/base/substitute.html)ed value of `expr`
  will be used when `expr` is evaluated. If `expr` is a quosure and you
  would like to use its expression as a value for `expr`, then you must
  set `quoted` to `TRUE`.

- outputArgs:

  A list of arguments to be passed through to the implicit call to
  [`uiOutput()`](https://rdrr.io/pkg/shiny/man/htmlOutput.html) when
  `renderUI` is used in an interactive R Markdown document.

## See also

[`userOutput`](userOutput.md) for the corresponding client side function
and examples.

Other user outputs: [`userOutput()`](userOutput.md)
