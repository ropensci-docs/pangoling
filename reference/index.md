# Package index

## About

- [`pangoling`](https://docs.ropensci.org/pangoling/reference/pangoling-package.md)
  [`pangoling-package`](https://docs.ropensci.org/pangoling/reference/pangoling-package.md)
  : pangoling: Access to Large Language Model Predictions

## Causal (or GPT-like) modeling

- [`causal_next_tokens_pred_tbl()`](https://docs.ropensci.org/pangoling/reference/causal_next_tokens_pred_tbl.md)
  : Generate next tokens after a context and their predictability using
  a causal transformer model
- [`causal_pred_mats()`](https://docs.ropensci.org/pangoling/reference/causal_pred_mats.md)
  : Generate a list of predictability matrices using a causal
  transformer model
- [`causal_words_pred()`](https://docs.ropensci.org/pangoling/reference/causal_predictability.md)
  [`causal_tokens_pred_lst()`](https://docs.ropensci.org/pangoling/reference/causal_predictability.md)
  [`causal_targets_pred()`](https://docs.ropensci.org/pangoling/reference/causal_predictability.md)
  : Compute predictability using a causal transformer model

## Masked (or BERT-like) modeling

- [`masked_targets_pred()`](https://docs.ropensci.org/pangoling/reference/masked_targets_pred.md)
  : Get the predictability of a target word (or phrase) given a left and
  right context
- [`masked_tokens_pred_tbl()`](https://docs.ropensci.org/pangoling/reference/masked_tokens_pred_tbl.md)
  : Get the possible tokens and their log probabilities for each mask in
  a sentence

## Helper functions for causal and masked models

- [`causal_config()`](https://docs.ropensci.org/pangoling/reference/causal_config.md)
  : Returns the configuration of a causal model

- [`causal_preload()`](https://docs.ropensci.org/pangoling/reference/causal_preload.md)
  : Preloads a causal language model

- [`masked_config()`](https://docs.ropensci.org/pangoling/reference/masked_config.md)
  : Returns the configuration of a masked model

- [`masked_preload()`](https://docs.ropensci.org/pangoling/reference/masked_preload.md)
  : Preloads a masked language model

- [`install_py_pangoling()`](https://docs.ropensci.org/pangoling/reference/install_py_pangoling.md)
  :

  Install the Python packages needed for `pangoling`

- [`installed_py_pangoling()`](https://docs.ropensci.org/pangoling/reference/installed_py_pangoling.md)
  :

  Check if the required Python dependencies for `pangoling` are
  installed

- [`set_cache_folder()`](https://docs.ropensci.org/pangoling/reference/set_cache_folder.md)
  : Set cache folder for HuggingFace transformers

## Vocabulary and tokenization

- [`ntokens()`](https://docs.ropensci.org/pangoling/reference/ntokens.md)
  : The number of tokens in a string or vector of strings
- [`tokenize_lst()`](https://docs.ropensci.org/pangoling/reference/tokenize_lst.md)
  : Tokenize an input
- [`transformer_vocab()`](https://docs.ropensci.org/pangoling/reference/transformer_vocab.md)
  : Returns the vocabulary of a model

## Others

- [`perplexity_calc()`](https://docs.ropensci.org/pangoling/reference/perplexity_calc.md)
  : Calculates perplexity
- [`df_jaeger14`](https://docs.ropensci.org/pangoling/reference/df_jaeger14.md)
  : Self-Paced Reading Dataset on Chinese Relative Clauses
- [`df_sent`](https://docs.ropensci.org/pangoling/reference/df_sent.md)
  : Example dataset: Two word-by-word sentences
