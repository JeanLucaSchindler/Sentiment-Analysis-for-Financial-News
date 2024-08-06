# README

## Sentiment Analysis for Financial News

### Overview

This project aims to classify financial news articles into three sentiment categories: **negative**, **neutral**, and **positive**. The model uses a combination of pre-trained embeddings and custom deep learning layers to achieve this classification.


<p align="center">
    <img src="https://www.mdpi.com/applsci/applsci-11-04443/article_deploy/html/images/applsci-11-04443-g001-550.jpg"
</p>

### Data Preparation

1. **Loading and Preprocessing Data:**
   - The dataset was loaded from a CSV file, containing financial news articles and their associated sentiments. The data was obtained from [this Kaggle dataset](https://www.kaggle.com/datasets/ankurzing/sentiment-analysis-for-financial-news)
   - The data was encoded in ISO-8859-1 and had no header, so columns were manually named as `sentiment` and `text`.
   - Sentiments were mapped to numerical labels: `negative` (0), `neutral` (1), and `positive` (2).

2. **Splitting Data:**
   - The data was split into training and validation sets using an 80/20 ratio.

3. **Data Formatting:**
   - Text data was extracted and ensured to be in the correct shape for input to the model.
   - Labels were flattened and one-hot encoded to match the output format of the model.

### Model Architecture

The model architecture comprises the following components:

1. **Universal Sentence Encoder (USE) Layer:**
   - A custom layer, `USELayerWithExpandDims`, was created to use the Universal Sentence Encoder (USE) for embedding the input texts.
   - The embeddings are expanded to a 3D tensor to feed into LSTM layers.

2. **Bidirectional LSTM Layers:**
   - Three bidirectional LSTM layers with 72 units each were used. These layers help in capturing the sequential dependencies in both directions.

3. **Dropout Layers:**
   - Dropout layers with a 50% dropout rate were added after each LSTM layer to prevent overfitting.

4. **Dense Output Layer:**
   - A Dense layer with 3 units and a softmax activation function was used for the final output, indicating the probability of each sentiment class.

### Model Training

- The model was compiled using the **categorical cross-entropy** loss function and the **Adam** optimizer. The accuracy metric was used to evaluate the model's performance.

- The model was trained for 10 epochs, using the training and validation datasets. The training process included monitoring the model's performance on the validation set.

### Results

- The model achieved an **accuracy of 77%** on the validation set, indicating a reasonable performance in classifying the financial news articles into the three sentiment categories.

### Additional Information

- The trained model can be saved and reloaded for future predictions. A sample set of custom news articles was also provided to test the model's predictions on unseen data.

- For further experimentation, different hyperparameters, additional layers, or alternative pre-trained models could be explored to potentially improve accuracy.

This project provides a foundation for sentiment analysis in financial news, with potential applications in financial markets and news analytics.
