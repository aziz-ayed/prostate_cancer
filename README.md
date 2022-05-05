# Leveraging longitidunal data to predict future PSA values

Research aiming at using previous PSA values, temporal features (BMI, comorbidities)  and static features (reports, race, age at diagnosis) to predict future PSA value

1. [Packages Used](#packages-used)
1. [Datasets](#datasets)
1. [Models](#models)

1. [Results](#results)


## Packages Used

- [numpy](https://github.com/numpy/numpy)
- [XGBoost](https://github.com/dmlc/xgboost)
- [Keras](https://github.com/keras-team/keras)
- [TensorFlow](https://github.com/tensorflow/tensorflow)
- [Optuna](https://github.com/optuna/optuna)


## Datasets

We used a dataset of patients from the MGH hospital. We first used a previous script to recover our cohort of interest (not included here because work of Madhur Nayan and his team). We then performed some work to recover PSA sequence end (which corresponds to treatment). See "Row Selection" block in preprocess_and_xgboost.ipynb. All the data preprocessing can be found in that same notebook and is commented to facilitate reproduction of our results. 

## Fonctions

All the important functions (eg. create window length, training/test split...) can be found in the "Utils" block of the notebook preprocess_and_xgboost.ipynb
In particular, to play with the window length there is a function "filter" that drops patients that don't have enough PSA values and the "window" function then performs all the data transformation at once returning X_train, y_train, X_test, y_test

## Models

Our BoW is trained on the MRI reports of the training patients and then applied to the test patients. The model and its parameters can be found in preprocess_and_xgboost.ipynb

XGBoost and the hypertuning function can be found in the "preprocess_and_xgboost.ipynb"
The CNNs and Tower models can be found in the google colab "neural_networks.ipynb" 

## Results

To reproduce the results one would have to play with the functions fitler and window the pre process the data in the right way and then run the models in the notebooks mentioned above. In particular retrain and hypertune XGBoost with the different parameters l. And retrain the CNN model with different parameters. Note that our train/test split function has a seed as default which would allow to recover the exact same results as mentioned in our report. 



