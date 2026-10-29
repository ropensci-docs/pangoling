# Returns the vocabulary of a model

Returns the (decoded) vocabulary of a model.

## Usage

``` r
transformer_vocab(
  model = getOption("pangoling.causal.default"),
  add_special_tokens = NULL,
  decode = FALSE,
  config_tokenizer = NULL
)
```

## Arguments

- model:

  Name of a pre-trained model or folder. One should be able to use
  models based on "gpt2". See [hugging face
  website](https://huggingface.co/models?other=gpt2).

- add_special_tokens:

  Whether to include special tokens. It has the same default as the
  [AutoTokenizer](https://huggingface.co/docs/transformers/v4.25.1/en/model_doc/auto#transformers.AutoTokenizer)
  method in Python.

- decode:

  Logical. If `TRUE`, decodes the tokens into human-readable strings,
  handling special characters and diacritics. Default is `FALSE`.

- config_tokenizer:

  List with other arguments that control how the tokenizer from Hugging
  Face is accessed.

## Value

A vector with the vocabulary of a model.

## See also

Other token-related functions:
[`ntokens()`](https://docs.ropensci.org/pangoling/reference/ntokens.md),
[`tokenize_lst()`](https://docs.ropensci.org/pangoling/reference/tokenize_lst.md)

## Examples

``` r
if (FALSE) { # installed_py_pangoling()
transformer_vocab(model = "gpt2") |>
 head()
}
```
