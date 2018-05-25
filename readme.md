# Entity Extraction and Disambiguition API
This repository is a modification of NeuroNER(Neuro Named Entity Recognition) NLP
package used for Entity Extraction and Disambiguition.

## Contents
- [Project Timeline](#project-timeline)
- [Model Overview](#model-overview)
- [Getting Started](#getting-started)
- [Training a Model](#training-a-model)
- [Evaluating a Model](#evaluating-a-model)
- [Using Pretrained Model for Prediction](#using-pretrained-model-for-prediction)

## Project Timeline
- Create Project Folder with all requirements :heavy_check_mark:
  1. NeuroNER model in ./NeuroNER
  2. GENIA Corpus dataset in ./GENIACorpus
  3. Required files in ./(xml-extractor.py, run.py)
  4. Run > pip3.5 install requirements.txt
- Create file to extract data from xml file (./xml-extractor.py) :heavy_check_mark:
- Prepare Training Data Set :heavy_check_mark:
  1. > python3.5 xml-extractor.py
  2. Data will be available in ./data/(train, valid, test)
- Train NeuroNER(Run the following commands) :heavy_check_mark:
  1. > cd NeuroNER/src
  2. > python3.5 main.py --parameters_filepath=../../parameters.ini
  3. Model will be trained for 30 epochs and the output will be save in ./output with corresponding folder name
- Test NeuroNER on Validation Set :heavy_check_mark:
  1. While model is trained it is automatically  validated
- Make Pre-trained Model :heavy_check_mark:
  1. Model is available at ./trained_models/genia_pretrained
  2. python3.5 main.py --train_model=False --use_pretrained_model=True --dataset_text_folder=../../data/<new_data_folder_name> --pretrained_model_folder=../../trained_models/genia_pretrained
- Improve the model :heavy_multiplication_x:
- Create an API to use the model :heavy_multiplication_x:


## Model Overview
The **NeuroNER** is a program that performs named-entity extraction(NER).
This model has been trained on GENIA Corpus with 2000 articles and 6 different classes:
1. Protiens
2. Genes
3. Compounds
4. Organisms
5. Cell Parts
6. Others
The pretrained model has been trained for 30 epochs

## Getting Started
In order to use this model, the following requirements(**requirements.txt**) have to be satisfied.
The requirements can be installed using the following command.
'''python3
pip3.5 install requirements.txt
'''
Make sure that you are using **Python 3.5** instead of any higher version as this model
runs on Python 3.5

**Then** clone the project and continue to data set preperation
'''
git clone https://gitlab.innoplexus.de/Innoplexus-Consulting-Services/EntityExtractorAPI.git
'''

## Data Set Preparation
You can use the following command to create the dataset for training:

'''python3
python3.5 xml-extractor.py
'''

The above command creates training, validation and testing datasets in ./data/(test, train, valid) folders.


## Training a Model

You can run the model in the following ways:
1. training mode(from scratch)
2. training mode(using pretrained model)
3. prediction mode(using pretrained model)

### parameters.ini file required.
For every type of model training a *requirements.txt* is a must. It can be stored
anywhere and specified during training from the terminal

### Training Mode(From Scratch)
run the following command
'''python3
cd NeuroNER/src
python3.5 main.py --parameters_filepath=../../parameters.ini
'''

## Evaluating a Model
NeuroNER comes with a good terminal and text(and pdf) based model evaluation results. You can find the model evaluations(accuracy, prediction, ...) in the output folder

## Using Pretrained Model for Prediction
A pretrained model has been created at ./trained_models/genia_pretrained
Run the following command to use the pretrained model
'''
cd NeuroNER/src
python3.5 main.py --train_model=False --use_pretrained_model=True --dataset_text_folder=../../data/<new_data_folder_name> --pretrained_model_folder=../../trained_models/genia_pretrained
'''
This assumes that the data is available in ./data/<new_data_folder_name>
