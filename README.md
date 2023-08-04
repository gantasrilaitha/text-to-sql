# text-to-sql
NLP project of identifying aggregates used in sql query and teanslate text to sql

We used wikisql and spider dataset.
Wikisql dataset can be downloaded from :https://drive.google.com/drive/folders/13f2MrdpieC9QGXM_DJnj2f1Hs6ZBh2ZT?usp=sharing
Spider dataset can be downloaded from :https://drive.google.com/uc?export=download&id=1TqleXec_OykOYFREKKtschzY29dUcVAQ

Worked with paraphrased wikisql dataset(used T5_Paraphrased_Paws pretrained model to paraphrase the questions in a way that its sematics remian unchanged.)We sliced the entire train & validation dataset of wikisql & performed paraphrasing.
All the paraphrased datasets are merged & Navie Bayes Classifier is applied to classify the aggregates (MIN,MAX,COUNT,AVG..)that would be used in SQL query.Obtained train & val accuracy of 87% and test accuracy of 82%.

For translation of text to SQL:
  a)Used unparaphrased wikisql dataset and applied SEQ2SEQ model to obtain simple queries(Evaluation metric used: BLU Score & Accuracy)
  b)Used spider dataset and applied pretrained BART model to achieve complex queries.(Evaluation metric used:Rouge Score)

bayes_wikisql.ipynb:contains bayes classifier to identify aggregates to be used in sql query
text_to_sql_wikisql_paraphrasing.ipynb: contains paraphrased wikisql dataset& implemented seq2seq model for sql generation
text_to_sql_spider_BART.ipynb: contians BART model for complex queries
text_to_sql_wikisql_w/oparaphrase.ipynb: contains seq2seq model for text to sql withouto paraphrasing the dataset
