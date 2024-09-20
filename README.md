# End_to_end_Masked_Language_Modeling_with_BERT

## Introduction
Masked Language Modeling is a fill-in-the-blank task, where a model uses the context words surrounding a mask token to try to predict what the masked word should be.For an input that contains one or more mask tokens, the model will generate the most likely substitution for each.
Example:
* Input: "I have watched this [MASK] and it was awesome."  
* Output: "I have watched this movie and it was awesome."

Masked language modeling is a great way to train a language model in a self-supervised setting (without human-annotated labels). Such a model can then be fine-tuned to accomplish various supervised NLP tasks.

### Dataset preparation
We will use the TextVectorization layer to vectorize the text into integer token ids. It transforms a batch of strings into either a sequence of token indices (one sample = 1D array of integer token indices, in order) or a dense representation  
(one sample = 1D array of float values encoding an unordered set of tokens).

###  Preprocessing functions
* The get_vectorize_layer function builds the TextVectorization layer.
* The encode function encodes raw text into integer token ids.
* The get_masked_input_and_labels function will mask input token ids. It masks 15% of all input tokens in each sequence at random.


### Create BERT model for MLM
We will create a BERT-like pretraining model architecture using the MultiHeadAttention layer. It will take token ids as inputs (including masked tokens) and it will predict the correct ids for the masked input tokens.

### Fine-tune a sentiment classification
Fine-tune self-supervised model on a downstream task of sentiment classification. To do this, let's create a classifier by adding a pooling layer and a Dense layer on top of the pre-trained BERT features.

### Conclusion
**The model achieved the following performance metrics after training**
* Training Loss: 0.5967
* Training Accuracy: 0.8446
* Validation Loss: 0.6064
* Validation Accuracy: 0.8439
