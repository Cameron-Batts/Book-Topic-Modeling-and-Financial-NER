# Book Topic Modeling and Financial Entity Extraction

**Author:** Cameron Batts  
**Tools:** Python · Gensim · NLTK · spaCy · pandas · NumPy

## Business Problem
Explore themes in a book collection and extract structured information from financial text, while checking whether model outputs are interpretable and useful.

## Project Approach
- Preprocess 16,559 name-reduced book summaries with POS-aware lemmatization.
- Train five- and ten-topic LDA models; compare two, three and five passes.
- Inspect topic terms and document mixtures.
- Demonstrate dependency parsing and financial NER across 4,846 news sentences.
- Distinguish baseline token counts from an optional raw-text, full-span extraction workflow.

## Key Findings
| Topics | Passes | Original corpus-fit score |
|---|---:|---:|
| 5 | 2 | 431.44 |
| 10 | 2 | 548.17 |
| 10 | 3 | 539.82 |
| 10 | 5 | 532.56 |

These are the supplied `2 ** (-log_perplexity)` values on the training corpus, not held-out performance. Five broad themes support overview browsing, while ten topics expose finer distinctions. Lower scores alone do not establish the best topic model.

Baseline NER produced suspicious tags, including `mn` as GPE and currency tokens as ORG. Destructive preprocessing and counting tokens rather than full entity spans limit interpretation. The revised full-span example is unexecuted.

## Run
```bash
python -m pip install -r requirements.txt
python -m spacy download en_core_web_md
jupyter lab notebooks/book_topics_and_financial_ner.ipynb
```
Place permitted local CSV copies in `data/`; see `data/README.md`. NLTK downloads its tagger and WordNet at runtime. Preprocessing and LDA training can take several minutes.

## Files
- `notebooks/book_topics_and_financial_ner.ipynb`: cleaned workflow and selected original outputs.
- `reports/book_topics_and_financial_ner.html`: readable analysis report.
- `reports/lda_corpus_fit.csv`: original LDA scores.
- `data/README.md`: local data requirements and attribution.
- `requirements.txt`: dependencies.
- `portfolio_card.html`: matching project card.

## Validation and Limitations
Code syntax checked; not rerun. Original numerical outputs are preserved; revised parsing and span-level NER do not have new results. No held-out topic evaluation, genre accuracy, NER accuracy or production improvement was measured. Dependencies are unpinned. Raw datasets, personal examples and local machine paths are omitted from the public package.

## Sources
CMU Book Summary Dataset: https://www.cs.cmu.edu/~dbamman/booksummaries.html . Financial PhraseBank source: Malo et al. (2014), *Good debt or bad debt: Detecting semantic orientations in economic texts*, https://doi.org/10.1002/asi.23062 . Retain attribution and observe applicable terms.

## Author
Cameron Batts  
GitHub: https://github.com/Cameron-Batts  
Portfolio: https://cameron-batts.github.io
