
# Phishing website detection

Phishing is a type of fraud in which an attacker impersonates a reputable company or person in order to get \
sensitive information such as login credentials or account information via email or other communication \
channels. Phishing is popular among attackers because it is easier to persuade someone to click a malicious \
link that appears to be authentic than it is to break through a computer's protection measures.The goal of \
this project is to create a ML solution to identify phishing websites. The final result of the project is a \
web application. It will take an a website's URL as input and classify the website: either yes (for phishing) \
or no (otherwise).

# Files' description
**.circleci:** contains code for circleci\
**additional_requirements.txt:** contains additional dependencies to install on top of the ones from requirements.txt
(during installing dependencies on Heroku time out error occurred due to many dependencies. Therefore dependencies, 
needed for the web app to run, are saved inside requirements.txt. The rest are in additional_requirements.txt)\
**app.py:** contains code for the web app\
**app_logging:** contains py files for a customized logging used for the project\
**App_Logs:** contains logging output for the web app\
**App_Output:** contains output of the web app to provide to an application user in case of multiple URLs 
provided in a csv/excel file format\
**App_Uploads:** directory for a csv/excel file provided by a web app user\
**best_model_finder:** contains code to create, tune, and select the best ML model\
**data_ingestion:** contains code to load data from Training_File_From_DB or Prediction_File_From_DB depending on a task\
**data_preprocessing:** contains code both for clustering and preproccessing applied to raw data\
**Dockerfile:** contains code implicitly used during deployment to create a docker container\
**Documents:** contains documentation which thoroughly describes the project\
**EDA:** contains exploratory data analysis\
**EncoderPickle:** contains all pickle files related to categorical/continuous (numeric) features, column dropping 
and feature standardization applied during training, and scaler used during KMeans clustering\
**extract_features:** contains code for feature extraction from a URL\
**Feature_Extractor_Logs:** contains log file generated during a URL feature extraction process\
**file_operations:** contains code for saving, loading, and finding an appropriate model file\
**flask_monitoringdashboard.db:** contains info from flask monitoring dashboard\
**main.py:** contains code which actually trains all ML models and code used for prediction 
(a user need to provide a folder name containing training or prediction data depending on a task,
locally postman can be used to do that via POST request)\
**Models:** contains the best trained model of each cluster

**Notice: there are 2 separate datasets for training and prediction. Prediction dataset is 
not used anywhere except for prediction. Despite this training data is splitted into train 
and test sets during model training process. Predicition dataset has been created applying code
from extract_features to some websites obtained from [PhishTank](https://community.opendns.com/phishtank/).
The training data comes from [here](https://data.mendeley.com/datasets/72ptz43s9v/1).**

**Prediction_Archive_Bad_Data:** contains archived prediction data files that have not passed data validation procedure\
**Prediction_Batch_Files:** contains preliminary data files for prediction task\
**prediction_data_insertion:** contains code for database table creation, data insertion, 
and data extraction from AstraDB\
**prediction_data_transformation:** contains data transformation code applied to validated data before database insertion\
**Prediction_File_From_DB:** contains data extracted from database for prediction\
**Prediction_Logs:** contains log files related to prediction process\
**Prediction_Output_File:** contains predictions for websites included in prediction dataset\
**prediction_raw_data_validation:** contains code to validate raw data from Prediction_Batch_Files\
**Prediction_Raw_Files_Validated:** contains validated data which actually is deleted after inserting into a database\
**prediction_validation_insertion.py:** contains code which launches validation and database 
insertion procedure for prediction data separately\
**predict_from_model.py:** contains code to obtain prediction from the best trained models for prediction dataset\
**Preprocessing_Data:** contains an image of the elbow plot for KMeans clustering\
**Procfile:** contains some necessary code used in deployment process by Heroku\
**requirements.txt:** contains dependencies for web app deployment process\
**runtime.txt:** contains python version used for the project (Heroku uses this to set up the python version)\
**schema_prediction.json:** prediction data schema for validation check\
**schema_training.json:** training data schema for validation check\
**static:** contains background image for the web app\
**templates:** contains the web app template\
**tests:** contains testing code (it contains nonthing in case of this project)\
**Training_Archive_Bad_Data:** contains archived training data files that have not passed data validation procedure\
**Training_Batch_Files:** contains preliminary data files for training task\
**training_data_insertion:** contains code for database table creation, data insertion, 
and data extraction from AstraDB\
**training_data_transformation:** contains data transformation code applied to validated data before database insertion\
**Training_File_From_DB:** contains data extracted from database for training\
**Training_Logs:** contains log files related to training process\
**training_model.py:** contains code to train and save the best model for each cluster\
**training_raw_data_validation:** contains code to validate raw data from Training_Batch_Files\
**Training_Raw_Files_Validated:** contains validated data which actually is deleted after inserting into a database\
**training_validation_insertion.py:** contains code which launches validation and database 
insertion procedure for training data separately\

## Deployment

The deployment is done using Heroku. CircleCi is used for CI/CD. 
The web app will be updated automatically if the code is updated on the github. 
The web app is available [here](https://phishing--detector.herokuapp.com/).

## Demo

![](https://github.com/VaheC/PhishingWebsiteDetection/blob/main/api.gif)

## Installation

If you have all packages from requirements.txt and additional_requirements.txt
installed on your pc , then you can run all the codes present in this project. 
    
## Run Locally
Install anaconda on your pc.\
Create a virtual environment in anaconda prompt. 

```bash
  conda -n env_name python=version

  example: conda -n phishing python=3.7

  python version can be taken from runtime.txt
```

Activate the virtual environment in anaconda prompt

```bash
  conda activate env_name 

  example: conda activate phishing 
```

Clone the project in command prompt

```bash
  cd <--provide any directory on your pc to clone git project-->
  example: cd C:\Users\Desktop\PhishingWebsiteDetection

  git clone https://git-link-to-project
```

Go to the cloned project directory on your pc 
in anaconda prompt

```bash
  cd directory-of-project

  example: cd C:\Users\Desktop\PhishingWebsiteDetection
```

Install dependencies in anaconda prompt

```bash
  pip install -r requirements.txt
  pip install -r additional_requirements.txt
```

Run the model building code in anaconda prompt

```bash
  python main.py
  use postman to send a folder name containing training data to main.py via POST request
```

Start the web app on your pc from anaconda prompt

```bash
  python app.py
```
Use http shown in anaconda prompt (the last line of 
output after running the code above) to open the web
app in a web browser.

```bash
  example: http://127.0.0.1:5000/
```
## Acknowledgements

- [How to write a Good readme](https://readme.so)
- [Video to gif converter](https://ezgif.com)
- [Video and audio merger](https://www.kapwing.com)
