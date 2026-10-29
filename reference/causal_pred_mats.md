# Generate a list of predictability matrices using a causal transformer model

This function computes a list of matrices, where each matrix corresponds
to a unique group specified by the `by` argument. Each matrix represents
the predictability of every token in the input text (`x`) based on
preceding context, as evaluated by a causal transformer model.

## Usage

``` r
causal_pred_mats(
  x,
  by = rep(1, length(x)),
  sep = " ",
  log.p = getOption("pangoling.log.p"),
  sorted = FALSE,
  model = getOption("pangoling.causal.default"),
  checkpoint = NULL,
  add_special_tokens = NULL,
  decode = FALSE,
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

- sorted:

  When default FALSE it will retain the order of groups we are splitting
  by. When TRUE then sorted (according to `by`) list(s) are returned.

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

- decode:

  Logical. If `TRUE`, decodes the tokens into human-readable strings,
  handling special characters and diacritics. Default is `FALSE`.

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

## Value

A list of matrices with tokens in their columns and the vocabulary of
the model in their rows

## Details

The function splits the input `x` into groups specified by the `by`
argument and processes each group independently. For each group, the
model computes the predictability of each token in its vocabulary based
on preceding context.

Each matrix contains:

- Rows representing the model's vocabulary.

- Columns corresponding to tokens in the group (e.g., a sentence or
  paragraph).

- By default, values in the matrices are the natural logarithm of word
  probabilities.

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
[`causal_words_pred()`](https://docs.ropensci.org/pangoling/reference/causal_predictability.md)

## Examples

``` r
if (FALSE) { # installed_py_pangoling()
data("df_sent")
df_sent
list_of_mats <- causal_pred_mats(
                       x = df_sent$word,
                       by = df_sent$sent_n,  
                       model = "gpt2"
                )

# View the structure of the resulting list
list_of_mats |> str()

# Inspect the last rows of the first matrix
list_of_mats[[1]] |> tail()

# Inspect the last rows of the second matrix
list_of_mats[[2]] |> tail()
}
```
