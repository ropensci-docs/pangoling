# Changelog

## pangoling 1.0.3

CRAN release: 2025-04-07

- Internal changes to comply with CRAN requirements.
- HF_HOME is used now to store the models rather than TRANSFORMERS_CACHE

## pangoling 1.0.2

- Internal changes: OMP THREAD LIMIT was set to 1.

## pangoling 1.0.1

#### New Features

- Added
  [`installed_py_pangoling()`](https://docs.ropensci.org/pangoling/reference/installed_py_pangoling.md)
  to check if required Python dependencies (`transformers` and `torch`)
  are installed.

#### Other changes

- Informative startup message if python dependencies not installed.
- Documentation examples won’t run if python dependencies not installed
- Articles are now pre-computed vignettes. See

## pangoling 1.0.0

- changed the ownership of the repo to ropensci
- deprecated functions are now defunct and have been replaced with their
  respective alternative functions

## pangoling 0.0.0.9011

- Added `word_n` argument in
  [`causal_words_pred()`](https://docs.ropensci.org/pangoling/reference/causal_predictability.md)
  to indicate word order of the texts.
- Allows for models with larger vocabulary than tokenizer.

## pangoling 0.0.0.9010

### New Features:

- Added `checkpoint` parameter to
  [`causal_preload()`](https://docs.ropensci.org/pangoling/reference/causal_preload.md)
  and
  [`masked_preload()`](https://docs.ropensci.org/pangoling/reference/masked_preload.md)
  to allow loading models from checkpoints.
- Introduced
  [`causal_next_tokens_pred_tbl()`](https://docs.ropensci.org/pangoling/reference/causal_next_tokens_pred_tbl.md),
  which replaces
  [`causal_next_tokens_tbl()`](https://docs.ropensci.org/pangoling/reference/pangoling-defunct.md)
  and provides improved predictability calculations.
- Added
  [`causal_words_pred()`](https://docs.ropensci.org/pangoling/reference/causal_predictability.md),
  [`causal_targets_pred()`](https://docs.ropensci.org/pangoling/reference/causal_predictability.md),
  and
  [`causal_tokens_pred_lst()`](https://docs.ropensci.org/pangoling/reference/causal_predictability.md)
  to compute predictability for words, phrases, or tokens, replacing
  [`causal_lp()`](https://docs.ropensci.org/pangoling/reference/pangoling-defunct.md)
  and
  [`causal_tokens_lp_tbl()`](https://docs.ropensci.org/pangoling/reference/pangoling-defunct.md).
- Introduced
  [`masked_tokens_pred_tbl()`](https://docs.ropensci.org/pangoling/reference/masked_tokens_pred_tbl.md),
  replacing
  [`masked_tokens_tbl()`](https://docs.ropensci.org/pangoling/reference/pangoling-defunct.md),
  for retrieving possible tokens and their log probabilities.
- Introduced
  [`masked_targets_pred()`](https://docs.ropensci.org/pangoling/reference/masked_targets_pred.md),
  replacing
  [`masked_lp()`](https://docs.ropensci.org/pangoling/reference/pangoling-defunct.md),
  for calculating predictability based on left and right context.
- Introduced
  [`transformer_vocab()`](https://docs.ropensci.org/pangoling/reference/transformer_vocab.md)
  with an optional `decode` parameter to return decoded tokenized words.
- **New dataset `df_jaeger14`**: Self-paced reading data on Chinese
  relative clauses.
- **New dataset `df_sent`**: Example dataset with two word-by-word
  sentences.
- **New vignette**: Added a worked-out example of a causal model.

### Enhancements:

- Added `sep` argument in
  [`causal_words_pred()`](https://docs.ropensci.org/pangoling/reference/causal_predictability.md)
  to support languages without spaces between words (e.g., Chinese).
- New `log.p` argument across multiple functions to specify how
  predictability is calculated (e.g., log base *e*, log base 2 for bits,
  or raw probabilities).
- Improved tokenization utilities:
  [`tokenize_lst()`](https://docs.ropensci.org/pangoling/reference/tokenize_lst.md)
  now supports decoded outputs via the `decode` parameter.
- Updated
  [`install_py_pangoling()`](https://docs.ropensci.org/pangoling/reference/install_py_pangoling.md)
  to enhance Python environment handling.
- Added
  [`perplexity_calc()`](https://docs.ropensci.org/pangoling/reference/perplexity_calc.md)
  for computing perplexity from probabilities.

### Deprecations:

- Deprecated
  [`causal_next_tokens_tbl()`](https://docs.ropensci.org/pangoling/reference/pangoling-defunct.md),
  [`causal_lp()`](https://docs.ropensci.org/pangoling/reference/pangoling-defunct.md),
  [`causal_tokens_lp_tbl()`](https://docs.ropensci.org/pangoling/reference/pangoling-defunct.md),
  and
  [`causal_lp_mats()`](https://docs.ropensci.org/pangoling/reference/pangoling-defunct.md).
  Use
  [`causal_next_tokens_pred_tbl()`](https://docs.ropensci.org/pangoling/reference/causal_next_tokens_pred_tbl.md),
  [`causal_targets_pred()`](https://docs.ropensci.org/pangoling/reference/causal_predictability.md),
  [`causal_words_pred()`](https://docs.ropensci.org/pangoling/reference/causal_predictability.md),
  and
  [`causal_pred_mats()`](https://docs.ropensci.org/pangoling/reference/causal_pred_mats.md)
  instead.
- Deprecated
  [`masked_tokens_tbl()`](https://docs.ropensci.org/pangoling/reference/pangoling-defunct.md)
  and
  [`masked_lp()`](https://docs.ropensci.org/pangoling/reference/pangoling-defunct.md).
  Use
  [`masked_tokens_pred_tbl()`](https://docs.ropensci.org/pangoling/reference/masked_tokens_pred_tbl.md)
  and
  [`masked_targets_pred()`](https://docs.ropensci.org/pangoling/reference/masked_targets_pred.md)
  instead.

## pangoling 0.0.0.9009

- Deprecated `.by` in favor of `by`.

## pangoling 0.0.0.9008

- Fix a bug when `.by` is unordered

## pangoling 0.0.0.9007

- [`set_cache_folder()`](https://docs.ropensci.org/pangoling/reference/set_cache_folder.md)
  function added.
- Message when the package loads.
- New troubleshooting vignette.

## pangoling 0.0.0.9006

- `causal_lp` get a `l_contexts` argument.
- Checkpoints work for causal models (not yet for masked models).
- Ropensci badge added.

## pangoling 0.0.0.9005

- Strings with no tokens no longer throw errors.
- Requires correct version of R.

## pangoling 0.0.0.9004

- Causal models accept batches.

## pangoling 0.0.0.9003

- bug in causal_tokens_lp_tbl fixed

## pangoling 0.0.0.9002

- minor function names to avoid conflict with other packages

## pangoling 0.0.0.9001

- Tons of stuff. Fully functional package now.

## pangoling 0.0.0.9000

- First release!
