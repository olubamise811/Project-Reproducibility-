# Project Reproducibility
## BAE: BERT-based Adversarial Examples for Text Classification

## About
This project is about reproducing a research paper titled; BAE: BERT-based Adversarial Examples for Text Classification. 
In the reproduction of this paper, textattack framework approach was used. 
wordLSTM, word CNN and a distilbert based model were trained on Rotten tomatoes & IMDB datasets from huggingface, 
then the model was attacked using TEXTFOOLER and BAE attack recipies. 

## Requirement
Python 3.6 or above

## Installaation
Cloning Text attack repository from github and navigate to TextAttack directory.
```
!git clone https://github.com/QData/TextAttack.git
%cd TextAttack
```
To install TextAttack in dev mode for further development
```
!pip install -e .[dev]
```
To install the TextAttack library along with optional dependencies 
```
!pip install textattack[tensorflow,optional]
```
To install the required TensorFlow library version 2.14
```
!pip install tensorflow==2.14
```
## Additional information
In the Textattack Directory with was downloaded from github repositoty,  navigate to Textattack>> transformations>>model_args.py. 
In the model_args.py, the code from line 282-291, should be replaced with the code below;
```
                            if model_class == "LSTMForClassification":

                    model = textattack.models.helpers.LSTMForClassification.from_pretrained(args.model)

                    model = textattack.models.wrappers.PyTorchModelWrapper(

                        model, model.tokenizer

                    )

                elif model_class == "WordCNNForClassification":

                    model = textattack.models.helpers.WordCNNForClassification.from_pretrained(args.model)

                    model = textattack.models.wrappers.PyTorchModelWrapper(

                        model, model.tokenizer

                    )
```
