# Translation of Text-To-Sql 
Translating natural language question to sel query wrt to database schema.
The goal is to create an effective system for generating SQL queries from textual questions, enabling natural language interfaces to databases.

## **Datasets Used**
- **WikiSQL Dataset**: [Download WikiSQL Dataset](https://drive.google.com/drive/folders/13f2MrdpieC9QGXM_DJnj2f1Hs6ZBh2ZT?usp=sharing)
- **Spider Dataset**: [Download Spider Dataset](https://drive.google.com/uc?export=download&id=1TqleXec_OykOYFREKKtschzY29dUcVAQ)

## **Methodology**
1. **Paraphrasing**: 
   - Utilized the T5_Paraphrased_Paws pretrained model to paraphrase the WikiSQL questions while maintaining their semantic meaning.
   - Performed paraphrasing on the entire training and validation datasets of WikiSQL.

2. **Classification**:
   - Merged all paraphrased datasets and applied a Naive Bayes Classifier to identify aggregates (e.g., MIN, MAX, COUNT, AVG) used in SQL queries.
   - Achieved a training and validation accuracy of 87% and a test accuracy of 82%.

3. **Text-to-SQL Translation**:
   
   1. **Simple Queries**: Applied a SEQ2SEQ model to the *unparaphrased WikiSQL* dataset to generate simple SQL queries. 
     - **Evaluation Metrics**: BLEU Score & Accuracy
     -  Achieved Bleu score of 0.2 using paraphrasing on wikisql dataset
     -  Achieved Bleu score of 0.12 without paraphrasing on wikisql dataset

   2. **Complex Queries**: Used the pretrained **BART**(fusion of BERT + GPT) model with the *Spider dataset* to generate complex SQL queries(joins and nested queries). 
     - **Evaluation Metrics**: ROUGE Score
     -  Achieved RougeL Score of 0.4 using spider dataset

## **Files**
- **[bayes_wikisql.ipynb]**: Implements Naive Bayes Classifier to identify aggregates for SQL queries.
- **[text_to_sql_wikisql_paraphrasing.ipynb]**: Contains the paraphrased WikiSQL dataset and the SEQ2SEQ model for SQL generation.
- **[text_to_sql_wikisql_woparaphrase.ipynb]**: Implements the SEQ2SEQ model for SQL generation using the original WikiSQL dataset without paraphrasing.
- **[text_to_sql_spider_BART.ipynb]**: Utilizes the BART model for generating complex SQL queries from the Spider dataset.
       
## **Future Enhancements**
- Include a voice enabled feature, that converts spoken questions to sql queries

