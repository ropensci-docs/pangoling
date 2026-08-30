# Example dataset: Two word-by-word sentences

This dataset contains two example sentences, split word-by-word. It is
structured to demonstrate the use of the `pangoling` package for
processing text data.

## Usage

``` r
df_sent
```

## Format

A data frame with 15 rows and 2 columns:

- sent_n:

  (integer) Sentence number, indicating which sentence each word belongs
  to.

- word:

  (character) Words from the sentences.

## See also

Other datasets:
[`df_jaeger14`](https://docs.ropensci.org/pangoling/reference/df_jaeger14.md)

## Examples

``` r
# Load the dataset
data("df_sent")
df_sent
#> # A tidytable: 15 × 2
#>    sent_n word   
#>     <int> <chr>  
#>  1      1 The    
#>  2      1 apple  
#>  3      1 doesn't
#>  4      1 fall   
#>  5      1 far    
#>  6      1 from   
#>  7      1 the    
#>  8      1 tree.  
#>  9      2 Don't  
#> 10      2 judge  
#> 11      2 a      
#> 12      2 book   
#> 13      2 by     
#> 14      2 its    
#> 15      2 cover. 
```
