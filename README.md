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
<b>Next:</b> annotation of “domain-specific” feature. The script then opens List of domain specific (reference set and the extended one).xlsx and compares every lemma list with the domain list. It adds a domain-specific column for every original column and writes “yes” or “no” for each lemma. <br>Finally, it saves the full table as Automatic annotations_rare_domain-specific_stanza.csv and Automatic annotations_rare_domain-specific_spacy.csv (in two versions, one uses stanza tokenizer/lemmatizer and one uses SpaCy).<br>
- It will also create two table with statistics and graphs for summary_statistics_stanza.csv and summary_statistics_spacy.csv<br>
- It creates statistics at the end for nr of unique words/lemmas/lost lemmas/domain-specific/rare for each language pair & machine translation tool<br>
  And separately statistics for the lost lemmas only to see their compoundness related to rare and domain-specific<br>
- Compares the results between two different pipelines<br>
- Compares the results between the automatic annotation and the manual annotation (table_1_manual_annotations.csv)<br>

<b>Other files:</b><br>
Process description on investigating rarity, domain specificity, relationship mt-rt.docx<br>
Data_master_text_clean_2.csv (Dataset of translated sentences)<br>
Manual_annotations_lost_lemmas_rarity_domain-specificity_relationships.xlsx<br>
Create list of the most common lemmas of English.ipynb<br>
Most common English lemmas.xlsx (list created with the script “Create list of the most common lemmas of English.ipynb”<br>
Manual annotations of relationships lost rare words<br>
Manual of relationships (rare lemmas) (here we should leave only the four columns [lemma/relationship/rt translation unit/rare (maybe this one is implied)]<br>
es_en_DEEP<br>
es_en_DEEPL<br>
es_en_GOOGLE<br>
es_en_TRANSFORMERS<br>
Domain-specific lemmas (manual reference set and Conflibert)<br>

