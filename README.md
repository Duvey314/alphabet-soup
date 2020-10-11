# Deep Learning and Neural Networks


## Table of contents
* [Overview](#overview)
* [Data](#data)
* [Methodology](#methodology)
* [Results](#results)

### Overview

This project explores the implementation of neural networks using the TensorFlow platform in Python. This includes implementing neural networks and deep neural networks across a number of different datasets, including image, natural language, and numerical datasets.

The challenge is the creation of a neural network for Alphabet Soup charity division. This network uses a CSV containing more than 34,000 organizations that have received various amounts of funding from Alphabet Soup over the years. The challenge is to create a binary classifier that is capable of predicting whether or not an applicant will be successful if funded by Alphabet Soup using the features collected in the dataset.

### Data
The data in the charity_data.csvc contains a number of columns that capture metadata about each organization such as the following:

* EIN and NAME—Identification columns
* APPLICATION_TYPE—Alphabet Soup application type
* AFFILIATION—Affiliated sector of industry
* CLASSIFICATION—Government organization classification
* USE_CASE—Use case for funding
* ORGANIZATION—Organization type
* STATUS—Active status
* INCOME_AMT—Income classification
* SPECIAL_CONSIDERATIONS—Special consideration for application
* ASK_AMT—Funding amount requested
* IS_SUCCESSFUL—Was the money used effectively

In this dataset we are looking at whether or not the projects were successful. Therefore, our target variable is the IS_SUCCESSFUL column. The EIN and NAME columns are identifiers so they can be dropped from the dataframe. That leaves everything else as a feature.

The first preprocessing step on this data is to bin categorical data that has more than 10 unique values. Application type was binned from 17 values to 9 by binning all the application types with less than 500 applicants. The classification column was binned from 15 values to 7 by binning all the classifications with less than 700 applicants.

Before one hot encoding the categorical values, I changed the datatype of the special considerations column from obj to int so that it wouldn't be split into two columns during the encoding. After this, I one hot encoded all of the categorical variables and then merged them with the numeric columns. This final dataset has 44 columns.

The data was then split into test and train sets and then scaled using the StandardScaler model.

### Methodology

The model I used for the neural network was TensorFlows keras sequential model. The number of neurons was three times the number of inputs (44) and used the relu activation function. The number of epochs was 50. Using a binary crossentropy loss model and the adam optimizer I achieved an accuracy of 73% and a loss of 55%. 

The first step I tried for optimization was to add a second layer of neurons. This layer had 88 neurons. The rest of the model remained the same. The accuracy and loss remained the same.

I then created a network of 3 layers each with 132 neurons and increased the number of epochs to 100. This slightly increased the accuracy to 74% but this seems to be the limit. 


### Results

It seems that there is a limit to the accuracy of the model. The accuracy of 73% is fairly good with something this abstract. This model can be used as a tool for helping the company decide which projects to fund but should not be used as the sole decider.
