# Self-Paced Reading Dataset on Chinese Relative Clauses

This dataset contains data from a self-paced reading experiment on
Chinese relative clause comprehension. It is structured to support
analysis of reaction times, comprehension accuracy, and surprisal values
across various experimental conditions in a 2x2 fully crossed factorial
design:

## Usage

``` r
data(df_jaeger14)
```

## Format

A tibble with 8,624 rows and 15 variables:

- subject:

  Participant identifier, a character vector.

- item:

  Trial item number, an integer.

- cond:

  Experimental condition, a character vector indicating variations in
  sentence structure (e.g., "a", "b", "c", "d").

- word:

  Chinese word presented in each trial, a character vector.

- wordn:

  Position of the word within the sentence, an integer.

- rt:

  Reaction time in milliseconds for reading each word, an integer.

- region:

  Sentence region or phrase type (e.g., "hd1", "Det+CL"), a character
  vector.

- question:

  Comprehension question associated with the trial, a character vector.

- accuracy:

  Binary accuracy score for the comprehension question (1 = correct, 0 =
  incorrect).

- correct_answer:

  Expected correct answer for the comprehension question, a character
  vector ("Y" or "N").

- question_type:

  Type of comprehension question, a character vector.

- experiment:

  Name of the experiment, indicating self-paced reading, a character
  vector.

- list:

  Experimental list number, for counterbalancing item presentation, an
  integer.

- sentence:

  Full sentence used in the trial with words marked for analysis, a
  character vector.

- surprisal:

  Model-derived surprisal values for each word, a numeric vector.

**Region codes in the dataset (column `region`)**:

- **N**: Main clause subject (in object-modifications only)

- **V**: Main clause verb (in object-modifications only)

- **Det+CL**: Determiner+classifier

- **Adv**: Adverb

- **VN**: RC-verb+RC-object (subject relatives) or RC-subject+RC-verb
  (object relatives)

  - Note: These two words were merged into one region after the
    experiment; they were presented as separate regions during the
    experiment.

- **FreqP**: Frequency phrase/durational phrase

- **DE**: Relativizer "de"

- **head**: Relative clause head noun

- **hd1**: First word after the head noun

- **hd2**: Second word after the head noun

- **hd3**: Third word after the head noun

- **hd4**: Fourth word after the head noun (only in
  subject-modifications)

- **hd5**: Fifth word after the head noun (only in
  subject-modifications)

**Notes on reading times (column `rt`)**:

- The reading time of the relative clause region (e.g., "V-N" or "N-V")
  was computed by summing up the reading times of the relative clause
  verb and noun.

- The verb and noun were presented as two separate regions during the
  experiment.

## Source

Jäger, L., Chen, Z., Li, Q., Lin, C.-J. C., & Vasishth, S. (2015). *The
subject-relative advantage in Chinese: Evidence for expectation-based
processing*. Journal of Memory and Language, 79–80, 97-120.
[doi:10.1016/j.jml.2014.10.005](https://doi.org/10.1016/j.jml.2014.10.005)

## Details

- **Factor I**: Modification type (subject modification; object
  modification)

- **Factor II**: Relative clause type (subject relative; object
  relative)

**Condition labels**:

- a\) subject modification; subject relative

- b\) subject modification; object relative

- c\) object modification; subject relative

- d\) object modification; object relative

## See also

Other datasets:
[`df_sent`](https://docs.ropensci.org/pangoling/reference/df_sent.md)

## Examples

``` r
# Basic exploration
head(df_jaeger14)
#> # A tidytable: 6 × 14
#>   subject  item cond  word   wordn    rt region question accuracy correct_answer
#>   <chr>   <int> <chr> <chr>  <int> <int> <fct>  <chr>       <int>          <int>
#> 1 1m1         1 a     那個       1   360 Det+CL 那個顧客聽說過…        1              1
#> 2 1m1         1 a     昨晚       2   359 Adv    那個顧客聽說過…        1              1
#> 3 1m1         1 a     揍了服務生…     3   344 VN     那個顧客聽說過…        1              1
#> 4 1m1         1 a     一頓       4   313 FreqP  那個顧客聽說過…        1              1
#> 5 1m1         1 a     的         5   297 DE     那個顧客聽說過…        1              1
#> 6 1m1         1 a     顧客       6   312 head   那個顧客聽說過…        1              1
#> # ℹ 4 more variables: question_type <int>, experiment <chr>, list <int>,
#> #   sentence <chr>

# Summarize reaction times by region
 library(tidytable)
#> 
#> Attaching package: ‘tidytable’
#> The following objects are masked from ‘package:stats’:
#> 
#>     dt, filter, lag
#> The following objects are masked from ‘package:base’:
#> 
#>     %in%, %notin%
df_jaeger14 |>
  group_by(region) |>
  summarize(mean_rt = mean(rt, na.rm = TRUE))
#> # A tidytable: 13 × 2
#>    region mean_rt
#>    <fct>    <dbl>
#>  1 N         614.
#>  2 V         538.
#>  3 Det+CL    513.
#>  4 Adv       541.
#>  5 VN        618.
#>  6 FreqP     603.
#>  7 DE        439.
#>  8 head      653.
#>  9 hd1       604.
#> 10 hd2       538.
#> 11 hd3       704.
#> 12 hd4       479.
#> 13 hd5       865.
```
