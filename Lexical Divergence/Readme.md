# Sentence-Level Lexical Divergence Evaluation

This repository contains a robust implementation of a sentence-level evaluation metric designed to measure **lexical divergence in machine-translated texts**, particularly for political and humanitarian domains. It complements traditional MT metrics (e.g., BLEU, METEOR, BERTScore) by identifying whether **domain-critical terms** were preserved, omitted, or semantically drifted.

## Repository Structure

```
├── Spanish_to_English/
│   ├── Deep/
│   ├── DeepL/
│   ├── Google_API/
│   └── OPUS/

├── Arabic_to_English/
│   ├── Deep/
│   ├── DeepL/
│   ├── Google_API/
│   └── OPUS/
```

Each subfolder contains translations from a specific MT system. The `sentence_pairs.csv` file in each folder holds aligned source and translated sentences.

## What Does the Script Do?

The `Lexical_DivergenceV4.ipynb` script computes **lexical divergence** based on:

- A predefined **conflict_lexicon.csv** of domain-specific terms (e.g., *ceasefire*, *rebels*, *intervention*)
- Contextual embeddings from **eventdata-utd/ConfliBERT-scr-uncased**
- Cosine similarity and match scoring to detect replacements or omissions of keywords

### Output Includes:
- `missing_terms_lexical.csv`: All source keywords that were omitted or semantically shifted
- `candidates_lexical.csv`: Best candidate match in the translated sentence
- `lexical_divergence_results.csv`: Final lexical scores and classification (Acceptable vs. Divergence)
- Plots and charts (distribution, classification bars, explanation flags)

## Input Requirements

- `sentence_pairs.csv`: Aligned file with two columns: `Original_EN` and `MT_EN`
- `conflict_lexicon.csv`: A single-column CSV of domain keywords

## How to Run

### Option 1: Jupyter Notebook (Recommended)

1. Open `Lexical_DivergenceV4.ipynb`
2. Update the `DATA_PATH` variable to your input directory
3. Run all cells

### Option 2: Convert to Script

```bash
jupyter nbconvert --to script Lexical_DivergenceV4.ipynb
python Lexical_DivergenceV4.py
```

## Dependencies

```bash
pip install pandas numpy nltk scikit-learn matplotlib seaborn sentence-transformers
```

Also download the required NLTK resources:

```python
import nltk
nltk.download('punkt')
nltk.download('wordnet')
nltk.download('stopwords')
```

## Key Benefits

- Sentence-level evaluation (not just word or n-gram overlap)
- Detects paraphrased or softened translations of high-risk terms
- Supports explainability via "LowSim" and "NoLexMatch" flags
- Compatible with GMM or static thresholds
- Ready for integration with domain-specific MT evaluation pipelines

## Outputs & Artifacts

- CSVs of results
- Score distributions
- Acceptable vs. Divergence classification charts
- Explanation flag frequency plots
- Summary statistics for reporting
