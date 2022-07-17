# NLP-Research
Here is a One VS Rest Document Classifier based on pre-trained BERT model. We loaded a pre-trained BERT model from Hugging Face and combined a linear layer above its outbput to get our final classification results. Here we only have 5 categoreis in total, so it would not be too complex to build a One VS Rest Classifier.<br>
## Data Prepare
The dataset leveraged is from BBC news website corresponding to stories in five topical areas from 2004-2005. It has 5 natrual classes: business, entertainment, politics, sport, technology. The data cleaning preocess for NLP project may contain several standard procedures:<br>
1.Remove punctuations<br>
2.Lowercase<br>
3.Remove stopwords<br>
4.Stemming<br>
5.Lemmatization<br>
