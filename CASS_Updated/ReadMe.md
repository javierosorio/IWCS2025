# Ultra CASS+ Evaluation Framework README

This README documents the Ultra CASS+ pipeline for evaluating machine translation (MT) divergence in United Nations conflict-related documents. It includes:

1. **Cell 1: Core CASS+ Evaluation Engine**
2. **Cell 2: Sentence-Level Aggregation & Term Type Breakdown**
3. **Cell 3: Visualization and Summary**

---

## 1. Core Evaluation: Ultra CASS+ Logic

**Purpose:**
To automatically detect and classify translation divergence between source and MT outputs using conflict terminology.

**Key Features:**

* Uses **Stanza** for POS tagging, lemmatization, and NER.
* Computes **CASS\_Score** using a weighted combination of:

  * Semantic similarity (ConfliBERT embeddings)
  * Lexicon match
  * Orthographic penalties (diacritic, char noise, weird Unicode)
* Supports **acronym detection** via:

  * Explicit CSV maps
  * Pattern-based expansion using capitalized word initials
* Captures **explanations**: `LowSim`, `NoLexMatch`, `NER_Drop`, `CharNoise`, etc.
* Includes fallback for GMM clustering or static threshold when necessary

**Key Inputs:**

* `sentence_pairs.csv`
* `conflict_lexicon.csv`
* `acronyms_expansions.csv` (optional)

**Key Outputs:**

* `mt_eval_CASS.csv`
* `missing_terms.csv`
* `cass_summary_stats.csv`

---

## 2. Enhanced Sentence-Level Aggregation & Term-Type Breakdown

**Purpose:**
To roll up CASS results by sentence ID and analyze performance by error types.

**Highlights:**

* Aggregates:

  * Count of divergence causes per sentence
  * Number of diacritic, orthographic, and abbreviation issues
  * NER or POS mismatches
* Outputs file with sentence-level metadata for correlation and document-wide error heatmaps

**Output:**

* `sentence_level_cass_summary.csv`

---

## 3. Visualization & Summary Analysis

**Purpose:**
To visualize the distribution of CASS classifications and identify major error types.

**Fixes & Features:**

* Uses **Seaborn with hue assignment** to avoid `palette=` deprecation
* Shows:

  * CASS score boxplots by classification type
  * Count plots for term divergence categories
  * Histogram of scores
* Helps diagnose sources of poor translations visually

**Output:**

* Boxplot: `CASS Score vs. Divergence Class`
* Histogram: `Distribution of CASS Scores`
* Countplot: `Explanation Frequency`

---

