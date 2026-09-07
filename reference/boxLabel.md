# Create a label for [box](box.md)

boxLabel is inserted in the label slot of [box](box.md).

## Usage

``` r
boxLabel(text, status, style = "default")
```

## Arguments

- text:

  Label text. In practice only few letters or a number.

- status:

  label color status. See
  <https://adminlte.io/themes/AdminLTE/pages/UI/general.html>. Valid
  statuses are defined as follows:

  - `primary`: \#3c8dbc

  - `success`: \#00a65a

  - `info`: \#00c0ef

  - `warning`: \#f39c12

  - `danger`: \#f56954

- style:

  label border style: "default" (rounded angles), "circle" or "square".
