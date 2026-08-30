# Preloads a masked language model

Preloads a masked language model to speed up next runs.

## Usage

``` r
masked_preload(
  model = getOption("pangoling.masked.default"),
  add_special_tokens = NULL,
  config_model = NULL,
  config_tokenizer = NULL
)
```

## Arguments

- model:

  Name of a pre-trained model or folder. One should be able to use
  models based on "bert". See [hugging face
  website](https://huggingface.co/models?other=bert).

- add_special_tokens:

  Whether to include special tokens. It has the same default as the
  [AutoTokenizer](https://huggingface.co/docs/transformers/v4.25.1/en/model_doc/auto#transformers.AutoTokenizer)
  method in Python.

- config_model:

  List with other arguments that control how the model from Hugging Face
  is accessed.

- config_tokenizer:

  List with other arguments that control how the tokenizer from Hugging
  Face is accessed.

## Value

Nothing.

## Details

A masked language model (also called BERT-like, or encoder model) is a
type of large language model that can be used to predict the content of
a mask in a sentence.

If not specified, the masked model that will be used is the one set in
specified in the global option `pangoling.masked.default`, this can be
accessed via `getOption("pangoling.masked.default")` (by default
"bert-base-uncased"). To change the default option use
`options(pangoling.masked.default = "newmaskedmodel")`.

A list of possible masked can be found in [Hugging Face
website](https://huggingface.co/models?pipeline_tag=fill-mask)

Using the `config_model` and `config_tokenizer` arguments, it's possible
to control how the model and tokenizer from Hugging Face is accessed,
see the python method
[`from_pretrained`](https://huggingface.co/docs/transformers/v4.25.1/en/model_doc/auto#transformers.AutoProcessor.from_pretrained)
for details. In case of errors check the status of
<https://status.huggingface.co/>

## See also

Other masked model helper functions:
[`masked_config()`](https://docs.ropensci.org/pangoling/reference/masked_config.md)

## Examples

``` r
if (FALSE) { # installed_py_pangoling()
causal_preload(model = "bert-base-uncased")
}
```
