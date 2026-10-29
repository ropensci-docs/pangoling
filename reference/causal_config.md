# Returns the configuration of a causal model

Returns the configuration of a causal model

## Usage

``` r
causal_config(
  model = getOption("pangoling.causal.default"),
  checkpoint = NULL,
  config_model = NULL
)
```

## Arguments

- model:

  Name of a pre-trained model or folder. One should be able to use
  models based on "gpt2". See [hugging face
  website](https://huggingface.co/models?other=gpt2).

- checkpoint:

  Folder of a checkpoint.

- config_model:

  List with other arguments that control how the model from Hugging Face
  is accessed.

## Value

A list with the configuration of the model.

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
[`causal_preload()`](https://docs.ropensci.org/pangoling/reference/causal_preload.md)

## Examples

``` r
if (FALSE) { # installed_py_pangoling()
causal_config(model = "gpt2")
}
```
