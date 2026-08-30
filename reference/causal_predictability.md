# Compute predictability using a causal transformer model

These functions calculate the predictability of words, phrases, or
tokens using a causal transformer model.

## Usage

``` r
causal_words_pred(
  x,
  by = rep(1, length(x)),
  word_n = NULL,
  sep = " ",
  log.p = getOption("pangoling.log.p"),
  ignore_regex = "",
  model = getOption("pangoling.causal.default"),
  checkpoint = NULL,
  add_special_tokens = NULL,
  config_model = NULL,
  config_tokenizer = NULL,
  batch_size = 1,
  ...
)

causal_tokens_pred_lst(
  texts,
  log.p = getOption("pangoling.log.p"),
  model = getOption("pangoling.causal.default"),
  checkpoint = NULL,
  add_special_tokens = NULL,
  config_model = NULL,
  config_tokenizer = NULL,
  batch_size = 1
)

causal_targets_pred(
  contexts,
  targets,
  sep = " ",
  log.p = getOption("pangoling.log.p"),
  ignore_regex = "",
  model = getOption("pangoling.causal.default"),
  checkpoint = NULL,
  add_special_tokens = NULL,
  config_model = NULL,
  config_tokenizer = NULL,
  batch_size = 1,
  ...
)
```

## Arguments

- x:

  A character vector of words, phrases, or texts to evaluate.

- by:

  A grouping variable indicating how texts are split into groups.

- word_n:

  Word order, by default this is the word order of the vector x.

- sep:

  A string specifying how words are separated within contexts or groups.
  Default is `" "`. For languages that don't have spaces between words
  (e.g., Chinese), set `sep = ""`.

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

- batch_size:

  Maximum number of sentences/texts processed in parallel. Larger
  batches increase speed but use more memory. Since all texts in a batch
  must have the same length, shorter ones are padded with placeholder
  tokens.

- ...:

  Currently not in use.

- texts:

  A vector or list of sentences or paragraphs.

- contexts:

  A character vector of contexts corresponding to each target.

- targets:

  A character vector of target words or phrases.

## Value

For `causal_targets_pred()` and `causal_words_pred()`, a named numeric
vector of predictability scores. For `causal_tokens_pred_lst()`, a list
of named numeric vectors, one for each sentence or group.

## Details

These functions calculate the predictability (by default the natural
logarithm of the word probability) of words, phrases or tokens using a
causal transformer model:

- **`causal_targets_pred()`**: Evaluates specific target words or
  phrases based on their given contexts. Use when you have explicit
  context-target pairs to evaluate, with each target word or phrase
  paired with a single preceding context.

- **`causal_words_pred()`**: Computes predictability for all elements of
  a vector grouped by a specified variable. Use when working with words
  or phrases split into groups, such as sentences or paragraphs, where
  predictability is computed for every word or phrase in each group.

- **`causal_tokens_pred_lst()`**: Computes the predictability of each
  token in a sentence (or group of sentences) and returns a list of
  results for each sentence. Use when you want to calculate the
  predictability of every token in one or more sentences.

See the [online
article](https://docs.ropensci.org/pangoling/articles/intro-gpt2.html)
in pangoling website for more examples.

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
[`causal_next_tokens_pred_tbl()`](https://docs.ropensci.org/pangoling/reference/causal_next_tokens_pred_tbl.md),
[`causal_pred_mats()`](https://docs.ropensci.org/pangoling/reference/causal_pred_mats.md)

## Examples

``` r
if (FALSE) { # installed_py_pangoling()
# Using causal_targets_pred
causal_targets_pred(
  contexts = c("The apple doesn't fall far from the",
               "Don't judge a book by its"),
  targets = c("tree.", "cover."),
  model = "gpt2"
)

# Using causal_words_pred
causal_words_pred(
  x = df_sent$word,
  by = df_sent$sent_n,
  model = "gpt2"
)

# Using causal_tokens_pred_lst
preds <- causal_tokens_pred_lst(
  texts = c("The apple doesn't fall far from the tree.",
            "Don't judge a book by its cover."),
  model = "gpt2"
)
preds

# Convert the output to a tidy table
suppressPackageStartupMessages(library(tidytable))
map2_dfr(preds, seq_along(preds), 
~ data.frame(tokens = names(.x), pred = .x, id = .y))
}
```
