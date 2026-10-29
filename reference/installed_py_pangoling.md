# Check if the required Python dependencies for `pangoling` are installed

This function verifies whether the necessary Python modules
(`transformers` and `torch`) are available in the current Python
environment.

## Usage

``` r
installed_py_pangoling()
```

## Value

A logical value: `TRUE` if both `transformers` and `torch` are installed
and accessible, otherwise `FALSE`.

## See also

Other helper functions:
[`install_py_pangoling()`](https://docs.ropensci.org/pangoling/reference/install_py_pangoling.md),
[`set_cache_folder()`](https://docs.ropensci.org/pangoling/reference/set_cache_folder.md)

## Examples

``` r
if (FALSE) { # \dontrun{
if (installed_py_pangoling()) {
 message("Python dependencies are installed.")
} else {
 warning("Python dependencies are missing. Please install `torch` and `transformers`.")
}
} # }
```
