# Calculates perplexity

Calculates the perplexity of a vector of (log-)probabilities.

## Usage

``` r
perplexity_calc(x, na.rm = FALSE, log.p = TRUE)
```

## Arguments

- x:

  A vector of log-probabilities.

- na.rm:

  Should missing values (including NaN) be removed?

- log.p:

  If TRUE (default), x are assumed to be log-transformed probabilities
  with base e, if FALSE x are assumed to be raw probabilities,
  alternatively log.p can be the base of other logarithmic
  transformations.

## Value

The perplexity.

## Details

If x are raw probabilities (NOT the default), then perplexity is
calculated as follows:

\$\$\left(\prod\_{n} x_n \right)^\frac{1}{N}\$\$

## Examples

``` r
probs <- c(.3, .5, .6)
perplexity_calc(probs, log.p = FALSE)
#> [1] 2.231443
lprobs <- log(probs)
perplexity_calc(lprobs, log.p = TRUE)
#> [1] 2.231443
```
