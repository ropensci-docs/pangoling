# Preloads a causal language model

Preloads a causal language model to speed up next runs.

## Usage

``` r
causal_preload(
  model = getOption("pangoling.causal.default"),
  checkpoint = NULL,
  add_special_tokens = NULL,
  config_model = NULL,
  config_tokenizer = NULL
)
```

## Arguments

- model:

  Name of a pre-trained model or folder. One should be able to use
  models based on "gpt2". See [hugging face
  website](https://huggingface.co/models?other=gpt2).

- checkpoint:

  Folder of a checkpoint.

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

## More details about causal models

A causal language model (also called GPT-like, auto-regressive, or
decoder model) is a type of large language model usually used for
text-generation that can predict the next word (or more accurately in
fact token) based on a preceding context.

If not specified, the causal model used will be the one set in the
global option `pangoling.causal.default`, this can be accessed via
`getOption("pangoling.causal.default")` (by default "gpt2"). To change
the default option use
`options(pangoling.causal.default = "newcausalmodel")`.

A list of possible causal models can be found in [Hugging Face
website](https://huggingface.co/models?pipeline_tag=text-generation).

Using the `config_model` and `config_tokenizer` arguments, it's possible
to control how the model and tokenizer from Hugging Face is accessed,
see the Python method
[`from_pretrained`](https://huggingface.co/docs/transformers/v4.25.1/en/model_doc/auto#transformers.AutoProcessor.from_pretrained)
for details.

In case of errors when a new model is run, check the status of
<https://status.huggingface.co/>

## See also

Other causal model helper functions:
[`causal_config()`](https://docs.ropensci.org/pangoling/reference/causal_config.md)

## Examples

``` r
if (FALSE) { # installed_py_pangoling()
causal_preload(model = "gpt2")
}
```
