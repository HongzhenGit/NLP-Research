# NLP-Research
Here is a One VS Rest Document Classifier based on pre-trained BERT model. We loaded a pre-trained BERT model from Hugging Face and combined a linear layer above its outbput to get our final classification results. Here we only have 5 categoreis in total, so it would not be too complex to build a One VS Rest Classifier.<br>
## Data Prepare
The dataset leveraged is from BBC news website corresponding to stories in five topical areas from 2004-2005. It has 5 natrual classes: business, entertainment, politics, sport, technology. The data cleaning preocess for a NLP project may contain several standard procedures: 1) Remove punctuations, 2) Lowercase texts, 3) Remove stopwords, 4) Stemming, 5) Lemmatization. However, only some special characters are removed from texts in our case, because it might be better to keep all components which could help understand the sentiment when applying BERT pretrained model.<br> 
## Model Building and Training
This nerual network classifier is developed on Pytorch platform and the loss function here is BCEWithLogitsLoss. This loss combines a Sigmoid layer and the BCELoss in one single class. This version is more numerically stable than using a plain Sigmoid followed by a BCELoss as, by combining the operations into one layer, the log-sum-exp trick is leveraged for numerical stability. For more information about this loss function, please refer:<br>
https://pytorch.org/docs/stable/generated/torch.nn.BCEWithLogitsLoss.html<br>
## 
