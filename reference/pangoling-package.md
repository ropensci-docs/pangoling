# pangoling: Access to Large Language Model Predictions

Provides access to word predictability estimates using large language
models (LLMs) based on 'transformer' architectures via integration with
the 'Hugging Face' ecosystem <https://huggingface.co/>. The package
interfaces with pre-trained neural networks and supports both
causal/auto-regressive LLMs (e.g., 'GPT-2') and masked/bidirectional
LLMs (e.g., 'BERT') to compute the probability of words, phrases, or
tokens given their linguistic context. For details on GPT-2 and causal
models, see Radford et al. (2019)
<https://storage.prod.researchhub.com/uploads/papers/2020/06/01/language-models.pdf>,
for details on BERT and masked models, see Devlin et al. (2019)
[doi:10.48550/arXiv.1810.04805](https://doi.org/10.48550/arXiv.1810.04805)
. By enabling a straightforward estimation of word predictability, the
package facilitates research in psycholinguistics, computational
linguistics, and natural language processing (NLP).

## Details

These options are used to control various aspects of the pangoling
package. Users can customize these options via the
[`options()`](https://rdrr.io/r/base/options.html) function by
specifying `pangoling.<option>` names.

- `pangoling.debug`: Logical; when `TRUE`, enables debugging mode.
  Default is `FALSE`.

- `pangoling.verbose`: Integer; controls the verbosity level (e.g., 0 =
  silent, 1 = minimal, 2 = detailed). Default is `2`.

- `pangoling.log.p`: Logical; if `TRUE` (default), pangoling outputs
  log-transformed probabilities with base e, if FALSE the output are raw
  probabilities. Alternatively `log.p` can be the base of other
  logarithmic transformations (e.g., base `1/2`, to get surprisal values
  in bits rather than predictability).

- `pangoling.cache`: A cache object created with
  [`cachem::cache_mem`](https://cachem.r-lib.org/reference/cache_mem.html),
  allowing you to specify the maximum size (in bytes) for cached
  objects. Default is `1024 * 1024^2` bytes (1 MB).

- `pangoling.causal.default`: Character string; specifies the default
  model for causal language processing. Default is `"gpt2"`.

- `pangoling.masked.default`: Character string; specifies the default
  model for masked language processing. Default is
  `"bert-base-uncased"`.

Use `options(pangoling.<option> = <value>)` to set these options in your
session.

## See also

Useful links:

- <https://docs.ropensci.org/pangoling/>

- <https://github.com/ropensci/pangoling>

- Report bugs at <https://github.com/ropensci/pangoling/issues>

## Author

**Maintainer**: Bruno Nicenboim <b.nicenboim@tilburguniversity.edu>
([ORCID](https://orcid.org/0000-0002-5176-3943))

Other contributors:

- Chris Emmerly \[contributor\]

- Giovanni Cassani \[contributor\]

- Lisa Levinson \[reviewer\]

- Utku Turk \[reviewer\]

## Examples

``` r
options(pangoling.verbose = FALSE) # Removes messages
options(pangoling.verbose = TRUE) # Show messages 
```
