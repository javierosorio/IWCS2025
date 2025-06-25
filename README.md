<h1>Are They Truly Lost? Diagnosing and Mitigating Rare Term Loss in Domain-Specific Machine Translation </h1>
<p>
  Machine translation (MT) in specialized domains often alters or omits rare and domain-specific terms, reducing semantic precision. We present a framework to diagnose and address lexical loss by combining human annotation and automated tools. By focusing on the UN Parallel Corpus, our study identifies over 16,000 lost lemmas (4,503 unique) in MT outputs from Spanish and Arabic into English and categorizes them along three axes: rarity, domain specificity, and semantic relationship to the replacement unit. Findings reveal that many losses result not from semantic gaps, but from spelling variants, acronym expansions, or encoding issues, cases that mislead standard rarity metrics. We propose Conflict-Adjusted Semantic Score (CASS), a new evaluation score using ConfliBERT to detect subtle divergence. Our taxonomy of loss types informs targeted interventions, and our ConfliBERT-based classifier enables scalable annotation of loss patterns. This work is grounded in human-in-the-loop analysis and offers a replicable path for domain-sensitive MT assessment. We highlight critical risks in Arabic–English MT and show that vocabulary simplification is often misrepresented as information loss by current metrics. Our tools and annotated dataset are publicly available for future research.
</p>

Here is a brief description of the folders and their purpose. The internal structure of each folder is described in detail within its corresponding README.md file.
  
# Rare lemmas types, domain-specificity and manual annotations files
This folder contains the manual annotations dataset for the **semantic relationships**, the resources needed to replicate the results and the automatic portion of the annotation of the domain-specificity and rarity.
  
# Lexical Divergence
This folder contains the files for the implementation of a sentence-level evaluation metric designed **to measure lexical divergence** in machine-translated texts, particularly for political and humanitarian domains. It complements traditional MT metrics (e.g., BLEU, METEOR, BERTScore) by identifying whether domain-critical terms were preserved, omitted, or semantically drifted.

# Automated Annotation of Semantic Relationships for Lost Terms in MT

This module automates the classification of **semantic relationships** between *lost rare lemmas* and their counterparts in machine translation (MT) output.
