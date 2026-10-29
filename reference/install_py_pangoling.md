# Install the Python packages needed for `pangoling`

`install_py_pangoling` function facilitates the installation of Python
packages needed for using `pangoling` within an R environment, utilizing
the `reticulate` package for managing Python environments. It supports
various installation methods, environment settings, and Python versions.

## Usage

``` r
install_py_pangoling(method = c("auto", "virtualenv", "conda"),
                     conda = "auto",
                     version = "default",
                     envname = "r-pangoling",
                     restart_session = TRUE,
                     conda_python_version = NULL,
                     ...,
                     pip_ignore_installed = FALSE,
                     new_env = identical(envname, "r-pangoling"),
                     python_version = NULL)
```

## Arguments

- method:

  A character vector specifying the environment management method.
  Options are 'auto', 'virtualenv', and 'conda'. Default is 'auto'.

- conda:

  Specifies the conda binary to use. Default is 'auto'.

- version:

  The Python version to use. Default is 'default', automatically
  selected.

- envname:

  Name of the virtual environment. Default is 'r-pangoling'.

- restart_session:

  Logical, whether to restart the R session after installation. Default
  is TRUE.

- conda_python_version:

  Python version for conda environments.

- ...:

  Additional arguments passed to
  [`reticulate::py_install`](https://rstudio.github.io/reticulate/reference/py_install.html).

- pip_ignore_installed:

  Logical, whether to ignore already installed packages. Default is
  FALSE.

- new_env:

  Logical, whether to create a new environment if `envname` is
  'r-pangoling'. Default is the identity of `envname`.

- python_version:

  Specifies the Python version for the environment.

## Value

The function returns `NULL` invisibly, but outputs a message on
successful installation.

## Details

This function automatically selects the appropriate method for
environment management and Python installation, with a focus on virtual
and conda environments. It ensures flexibility in dependency management
and Python version control. If a new environment is created, existing
environments with the same name are removed.

## See also

Other helper functions:
[`installed_py_pangoling()`](https://docs.ropensci.org/pangoling/reference/installed_py_pangoling.md),
[`set_cache_folder()`](https://docs.ropensci.org/pangoling/reference/set_cache_folder.md)

## Examples

``` r

# Install with default settings:
if (FALSE) { # \dontrun{
 install_py_pangoling()
} # }
```
