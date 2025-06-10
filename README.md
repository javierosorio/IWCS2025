<h1>Are They Truly Lost? Diagnosing and Mitigating Rare Term Loss in Domain-Specific Machine Translation </h1>
<p>
  Machine translation (MT) in specialized domains often alters or omits rare and domain-specific terms, reducing semantic precision. We present a framework to diagnose and address lexical loss by combining human annotation and automated tools. By focusing on the UN Parallel Corpus, our study identifies over 16,000 lost lemmas (4,503 unique) in MT outputs from Spanish and Arabic into English and categorizes them along three axes: rarity, domain specificity, and semantic relationship to the replacement unit. Findings reveal that many losses result not from semantic gaps, but from spelling variants, acronym expansions, or encoding issues, cases that mislead standard rarity metrics. We propose Conflict-Adjusted Semantic Score (CASS), a new evaluation score using ConfliBERT to detect subtle divergence. Our taxonomy of loss types informs targeted interventions, and our ConfliBERT-based classifier enables scalable annotation of loss patterns. This work is grounded in human-in-the-loop analysis and offers a replicable path for domain-sensitive MT assessment. We highlight critical risks in Arabic–English MT and show that vocabulary simplification is often misrepresented as information loss by current metrics. Our tools and annotated dataset are publicly available for future research.
</p>

<p>
  Here is a brief description of the folders, files and their purpose:
  <h2>Rare lemmas types, domain-specificity and manual annotations files</h2>
  The resources needed to replicate the results (the automatic portion) and the file/s with the manual annotations.
  <h2>Lexical Divergence</h2>
   
</p>
