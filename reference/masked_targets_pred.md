# Get the predictability of a target word (or phrase) given a left and right context

Get the predictability (by default the natural logarithm of the word
probability) of a vector of target words (or phrase) given a vector of
left and of right contexts using a masked transformer.

## Usage

``` r
masked_targets_pred(
  prev_contexts,
  targets,
  after_contexts,
  log.p = getOption("pangoling.log.p"),
  ignore_regex = "",
  model = getOption("pangoling.masked.default"),
  checkpoint = NULL,
  add_special_tokens = NULL,
  config_model = NULL,
  config_tokenizer = NULL
)
```

## Arguments

- prev_contexts:

  Left context of the target word in left-to-right written languages.

- targets:

  Target words.

- after_contexts:

  Right context of the target in left-to-right written languages.

- log.p:

  Base of the logarithm used for the output predictability values. If
  `TRUE` (default), the natural logarithm (base *e*) is used. If
  `FALSE`, the raw probabilities are returned. Alternatively, `log.p`
  can be set to a numeric value specifying the base of the logarithm
  (e.g., `2` for base-2 logarithms). To get surprisal in bits (rather
  than predictability), set `log.p = 1/2`.

- ignore_regex:

  Can ignore certain characters when calculating the log probabilities.
  For example `^[[:punct:]]$` will ignore all punctuation that stands
  alone in a token.

- model:

  Name of a pre-trained model or folder. One should be able to use
  models based on "bert". See [hugging face
  website](https://huggingface.co/models?other=bert).

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

A named vector of predictability values (by default the natural
logarithm of the word probability).

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

## More examples

See the [online
article](https://docs.ropensci.org/pangoling/articles/intro-bert.html)
in pangoling website for more examples.

## See also

Other masked model functions:
[`masked_tokens_pred_tbl()`](https://docs.ropensci.org/pangoling/reference/masked_tokens_pred_tbl.md)

## Examples

``` r
if (FALSE) { # installed_py_pangoling()
masked_targets_pred(
  prev_contexts = c("The", "The"),
  targets = c("apple", "pear"),
  after_contexts = c(
    "doesn't fall far from the tree.",
    "doesn't fall far from the tree."
  ),
  model = "bert-base-uncased"
)
}
```
