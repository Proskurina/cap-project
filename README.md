[![CircleCI](https://circleci.com/gh/Proskurina/project-ml.svg?style=svg)](https://circleci.com/gh/Proskurina/project-ml)

## Project Overview

Project includes a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). This project operationalizes a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

## Setup the Environment

* Run `make setup` to create a virtualenv and activate it
* Run `make install` to install the necessary dependencies

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`

### Kubernetes Steps

* Setup and Configure Docker locally
* Setup and Configure Kubernetes locally
* Create Flask app in Container
* Run via kubectl


### Files

This repo includes 
- `app.py` file, `model_data` folder -  a Python flask app—in that serves out predictions (inference) about housing prices through API calls
- `Makefile` - contains some useful commands to setup and test the project
- `Dockerfile` - with commands to assemble a docker image
- `run_docker.sh` and `run_kubernetes.sh` files - scripts to run app in docker and in kubernetes respectively
