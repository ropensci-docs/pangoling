# Generate next tokens after a context and their predictability using a causal transformer model

This function predicts the possible next tokens and their predictability
(log-probabilities by default). The function sorts tokens in descending
order of their predictability.

## Usage

``` r
causal_next_tokens_pred_tbl(
  context,
  log.p = getOption("pangoling.log.p"),
  decode = FALSE,
  model = getOption("pangoling.causal.default"),
  checkpoint = NULL,
  add_special_tokens = NULL,
  config_model = NULL,
  config_tokenizer = NULL
)
```

## Arguments

- context:

  A single string representing the context for which the next tokens and
  their predictabilities are predicted.

- log.p:

  Base of the logarithm used for the output predictability values. If
  `TRUE` (default), the natural logarithm (base *e*) is used. If
  `FALSE`, the raw probabilities are returned. Alternatively, `log.p`
  can be set to a numeric value specifying the base of the logarithm
  (e.g., `2` for base-2 logarithms). To get surprisal in bits (rather
  than predictability), set `log.p = 1/2`.

- decode:

  Logical. If `TRUE`, decodes the tokens into human-readable strings,
  handling special characters and diacritics. Default is `FALSE`.

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

A table with possible next tokens and their log-probabilities.

## Details

The function uses a causal transformer model to compute the
predictability of all tokens in the model's vocabulary, given a single
input context. It returns a table where each row represents a token,
along with its predictability score. By default, the function returns
log-probabilities in natural logarithm (base *e*), but you can specify a
different logarithm base (e.g., `log.p = 1/2` for surprisal in bits).

If `decode = TRUE`, the tokens are converted into human-readable
strings, handling special characters like accents and diacritics. This
ensures that tokens are more interpretable, especially for languages
with complex tokenization.

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

Other causal model functions:
[`causal_pred_mats()`](https://docs.ropensci.org/pangoling/reference/causal_pred_mats.md),
[`causal_words_pred()`](https://docs.ropensci.org/pangoling/reference/causal_predictability.md)

## Examples

``` r
if (FALSE) { # installed_py_pangoling()
causal_next_tokens_pred_tbl(
  context = "The apple doesn't fall far from the",
  model = "gpt2"
)
}
```
