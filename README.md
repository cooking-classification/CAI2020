# Neural Cooking

Neural models revisiting the DEFT (Defi Fouille de Texte) 2013 shared task, using embedding approaches and deep architectures. 

The DEFT 2013 shared task addressed the general task of mining cooking recipes in French through several classification and information extraction tasks. 

Task 1 addressed the classification of recipes into four levels of difficulty *i.e.* Very Easy, Easy, Fairly Difficult, and Difficult. 
Task 2 addressed the classification of recipes based on the type of dish which can be Starter, Main Dish, and Dessert. 

**Source code associated to the Canadian AI 2020 submission.**

The "data" folder contains data for training, validation, and testing.
The "features" folder contains linguistic features that are used by the linguistic sub-model.
The "saved_models" folder includes the trained models whose results were reported in the LREC2020 submission.
The requirement.txt contains a dump of all necessary dependencies to run this code. It can be installed with pip using: `pip install -r requirements.txt`.
The trained models are stored using git lfs

# Running saved_models on Test Set

To reproduce the results of reported models:

1. Run the "test_embedder.ipynb". In this file, define embedding type and maximum number of words in each recipe. The code will create embeddings for the test set and will save them in the "embeddings" folder.
2. Run the file "test.ipynb", which loads the already saved_models, as well as already saved embeddings and runs the models one by one on the test data. For each saved model, micro and macro results on classes as well as F1 scores on individual classes are reported.

Note: we recommend the use of *Jupyter Lab*, as opposed to the classic jupyter notebook to avoid some bugs.

# Training New Models

To train a new model:

1. Run the "train_embedder.ipynb". In this file, define embedding type and maximum number of words per recipe. The code will create embeddings for the training and dev sets and will save them in the "embeddings" folder.
2. Run the file "train.ipynb", with desired hyperparameters. The embeddings which were created in the previous step are loaded and training starts. The model which achieves the best micro F1 score on the dev set, is saved in the "saved_models" folder.