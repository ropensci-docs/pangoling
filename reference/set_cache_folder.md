# Set cache folder for HuggingFace transformers

This function sets the cache directory for HuggingFace transformers. If
a path is given, the function checks if the directory exists and then
sets the `HF_HOME` environment variable to this path. If no path is
provided, the function checks for the existing cache directory in a
number of environment variables. If none of these environment variables
are set, it provides the user with information on the default cache
directory.

## Usage

``` r
set_cache_folder(path = NULL)
```

## Arguments

- path:

  Character string, the path to set as the cache directory. If NULL, the
  function will look for the cache directory in a number of environment
  variables. Default is NULL.

## Value

Nothing is returned, this function is called for its side effect of
setting the `HF_HOME` environment variable, or providing information to
the user.

## See also

[Installation
docs](https://huggingface.co/docs/transformers/installation?highlight=transformers_cache#cache-setup)

Other helper functions:
[`install_py_pangoling()`](https://docs.ropensci.org/pangoling/reference/install_py_pangoling.md),
[`installed_py_pangoling()`](https://docs.ropensci.org/pangoling/reference/installed_py_pangoling.md)

## Examples

``` r
if (FALSE) { # installed_py_pangoling()
if (FALSE) { # \dontrun{
set_cache_folder("~/new_cache_dir")
} # }
}
```
