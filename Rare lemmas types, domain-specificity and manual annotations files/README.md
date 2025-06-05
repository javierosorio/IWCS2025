<h1>This folder contains the resources needed to <strong>replicate the results</strong> (the automatic portion) and </i>the file/s with the manual annotations</i>.</h1>

<b>STEP 1.</b> Make sure you have in the same folder with the scripts these files:<br>
-	Dataset with the translated sentences <b>“data_master_text_clean_2.csv”</b><br>
  <b>***</b> For your own dataset upload your dataset and change the name of the csv file above to your own file name and change the name of the columns in the script based on your file in the script <i>“Create resouces, automatic annotation for domain, rare and comparison.ipynb”</i>]

- Download the file from “https://www.kaggle.com/datasets/rtatman/english-word-frequency" in the same folder as the script.<br>
- The list of domain-specific words present here <b>“List of domain specific (reference set and the extended one).xlsx”</b>. <br>For another domain other than political conflict, use your own reference list. 

<b>STEP 2.</b> Run the script <i>“Create list of the most common lemmas of English (non-mod,stanza).ipynb”</i> [This script will lemmatize the English Word Frequency list, will sum the frequency for the same lemmas in one, eliminate the duplicates, will calculate the times per million according to OED frequency bands and will keep only the most common lemmas and their times per million. The list will be used by the other script “Create resouces, automatic annotation for domain,rare and comparison.ipynb” to annotate the rarity feature of the lemmas].  
The output will be the file “Most common English lemmas.xlsx”.<br>
<b>STEP 3.</b> Run the script <i>“Create resouces, automatic annotation for domain,rare and comparison.ipynb”</i>
[The script opens data_master_text_clean_2.csv and selects the columns en, es_en_DEEP, es_en_DEEPL, es_en_GOOGLE, es_en_TRANSFOMERS, ar_en_DEEP, ar_en_DEEPL, ar_en_GOOGLE, and ar_en_TRANSFORMERS and:
<br>- The script runs the Stanza tokenizer and lemmatizer on each cell. It lists the unique words for every column together with their frequencies. It also lists the unique lemmas for every column and their frequencies. It then creates the column lost lemmas_en, which holds the words that appear only in the en column and their frequencies.<br>
<b>Next:</b> annotation of “rare” feature. The script opens Most common English lemmas.xlsx and checks every lemma list. It writes “yes” for lemmas that appear in the common list. It writes “no,” followed by the “times per million” value, for lemmas that do not appear.<br>
<b>Next:</b> annotation of “domain-specific” feature. The script then opens List of domain specific (reference set and the extended one).xlsx and compares every lemma list with the domain list. It adds a domain-specific column for every original column and writes “yes” or “no” for each lemma. <br><b>Finally</b>, it saves the full table as Automatic annotations_rare_domain-specific_stanza.csv and Automatic annotations_rare_domain-specific_spacy.csv (in two versions, one uses stanza tokenizer/lemmatizer and one uses SpaCy).<br>
- It will also create two table with statistics and graphs for summary_statistics_stanza.csv and summary_statistics_spacy.csv<br>
- It creates statistics at the end for nr of unique words/lemmas/lost lemmas/domain-specific/rare for each language pair & machine translation tool<br>
  And separately statistics for the lost lemmas only to see their compoundness related to rare and domain-specific<br>
- Compares the results between two different pipelines<br>
- Compares the results between the automatic annotation and the manual annotation (table_1_manual_annotations.csv)<br>

<b>Other files:</b><br>
- The script "Domain-specificity score using ConfliBERT.ipynb" calculates how similar words from your dataset are to a set of reference words related to political conflict and violence. It uses the ConfliBERT language model and stanza lemmatizer to create embeddings. The script then saves a similarity score to a new Excel file.
- Process description on investigating rarity, domain specificity, relationship mt-rt.docx<br>
- Data_master_text_clean_2.csv (Dataset of translated sentences)<br>
- Human annotations of relationships lost rare words(allMTT).xlsx<br>
(This file contains three sheets: 1) Human/manual annotations of the lost rare lemmas (domain-specificity&relationships between the lost lemma and the translation unit that represents it in MT version. Sheet2) Table of statistics of these annotations and percentages (lost/rare/domain-specific). Sheet3) Table of statistics of these annotations for the relationships between the abovementioned (lost lemma/ translation unit in MT version).
  - Another 4 files contain the annotation of the relationship between translation units only for the rare lemmas
- Create list of the most common lemmas of English.ipynb<br>
- Most common English lemmas.xlsx (list created with the script “Create list of the most common lemmas of English.ipynb”<br>
- Domain-specific lemmas (manual reference set and Conflibert)<br>

- The folder "Tables, graphs' contains:<br>
    - "Table statistics manual annotations.xlsx", the table with the statistics of the human annotations (based on "Human annotations of relationships lost rare words(allMTT).xlsx") for the rare words in two sheets:<br>
        - Lost_domain_rare (contains numbers about: Total nr. of unique words: <br>
                -- Total nr. of unique lemmas (stanza)<br>
                -- % of Total nr. of unique words<br>
                -- Rare (in unique lemmas)<br>
                -- % of total nr. Of unique lemmas (Stanza)<br>
                -- Domain-specific (in unique lemmas)<br>
                -- % of total nr. Of unique lemmas (Stanza)<br>
               <br> LOST LEMMAS</b><br>
                -- LOST lemmas<br>
                -- % of total nr. Of unique lemmas (Stanza)<br>
                -- Lost & Rare<br>
                -- % of  LOST lemmas<br>
                -- Lost & Domain-specific<br>
                -- % of  LOST lemmas<br>
                -- Lost & Rare & domain-specific<br>
                -- % of domain-specific in rare<br>
      - Relationships: Numbers related to the relationships between lost the RARE lost lemmas and representing translation uni / language pairs and MT tools used for the machine translated version, grouped in 7 main groups:
                  -- Spelling or version variant<br>
                  -- Abbreviation or acronym relation<br>
                  -- Character set issue<br>
                  -- Missing information<br>
                  -- Semantic equivalence<br>
                  -- Technical issue, Unclear)<br>



