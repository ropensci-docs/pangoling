# Tokenize an input

Tokenize a string or token ids.

## Usage

``` r
tokenize_lst(
  x,
  decode = FALSE,
  model = getOption("pangoling.causal.default"),
  add_special_tokens = NULL,
  config_tokenizer = NULL
)
```

## Arguments

- x:

  Strings or token ids.

- decode:

  Logical. If `TRUE`, decodes the tokens into human-readable strings,
  handling special characters and diacritics. Default is `FALSE`.

- model:

  Name of a pre-trained model or folder. One should be able to use
  models based on "gpt2". See [hugging face
  website](https://huggingface.co/models?other=gpt2).

- add_special_tokens:

  Whether to include special tokens. It has the same default as the
  [AutoTokenizer](https://huggingface.co/docs/transformers/v4.25.1/en/model_doc/auto#transformers.AutoTokenizer)
  method in Python.

- config_tokenizer:

  List with other arguments that control how the tokenizer from Hugging
  Face is accessed.

## Value

A list with tokens

## See also

Other token-related functions:
[`ntokens()`](https://docs.ropensci.org/pangoling/reference/ntokens.md),
[`transformer_vocab()`](https://docs.ropensci.org/pangoling/reference/transformer_vocab.md)

## Examples

``` r
if (FALSE) { # installed_py_pangoling()
tokenize_lst(x = c("The apple doesn't fall far from the tree."), 
             model = "gpt2")
}
```
