# NLP-Research
Here is an One VS Rest Document Classifier based on pre-trained BERT model. We loaded this pre-trained model from Hugging Face and followed a linear layer after it to get a binary classifier. Here we only have 5 categoreis in total, so it would not be too complex to build a One VS Rest Multi-Category Classifier.<br>
## Data Preparation
The dataset leveraged is from BBC news website corresponding to stories in five topical areas from 2004-2005. It has 5 natrual classes: business, entertainment, politics, sport, technology. The data cleaning preocess for a NLP project may contain several standard procedures: 1) Remove punctuations, 2) Lowercase texts, 3) Remove stopwords, 4) Stemming, 5) Lemmatization. However, only some special characters are removed from texts in our case, because it might be better to keep all components which could help understand the sentiment when applying BERT pretrained model.<br> 
This nerual network classifier is developed on Pytorch platform. The Dataset and DataLoader classes from Pytroch are used to provide batches of data when performing model training and validation. To do this, a CustomDataset inherited from the Dataset class class should be defined, and within this CustomDataset, one should speficify how the data should be prepared or manipulated for the NN model. 
## Nerual Network Design
The NN designed in this trail consists of three layers:<br>
1. The pre-trained BERT layer(transform the texts into numerical vectors)<br>
2. A dropout layer with probability of 0.3(an effective technique for regularization and preventing the co-adaptation of neurons)<br>
3. A linear layer to get the final output<br>

The loss function selected is BCEWithLogitsLoss. This loss function combines a Sigmoid layer and the BCELoss in one single class. For more information about this loss function, please refer: https://pytorch.org/docs/stable/generated/torch.nn.BCEWithLogitsLoss.html<br>
## Model Training and Validation
After the loss is calculated by BCEWithLogitsLoss, an Adam optimizer is applyed to do the backward propagation paramater updating. After servel EPOCHs, the loss on validation set will start to increase, and this is the time point where the model training should be stopped(early stopping). Once all binary classifiers(for each category) are well-trained, an One VS Rest multi-category classifier could be constructed by combining them together: a sample would be grouped into the corresponding class of a classifer that gives the largest score.<br>
To evaluate the performance of each binary classifier, the Precision and Recall Rates by thresholds and the loss on Validation and Training sets are illustrated:<br>
![Binary Classifier Evaluation](https://github.com/HongzhenGit/NLP-Research/blob/main/Assets/Binary%20Claasifier%20Performance.png)<br>
The performance of the final One VS Rest Classifier could be validated through a confusion matrix:<br>
![Confusion Matrix](https://github.com/HongzhenGit/NLP-Research/blob/main/Assets/One%20VS%20Rest%20Classifier%20Heatmap.png)<br>
***For more details and codes, please check my notebook.***
