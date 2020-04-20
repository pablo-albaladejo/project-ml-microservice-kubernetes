[![CircleCI](https://circleci.com/gh/pablo-albaladejo/project-ml-microservice-kubernetes.svg?style=svg)](https://circleci.com/gh/pablo-albaladejo/project-ml-microservice-kubernetes)


## Project Overview

In this project, I have applied the skills I have acquired at Cloud DevOps NanoDegree to operationalize a Machine Learning Microservice API.

I'm given a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). This project demonstrates my ability to operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

### Project Tasks

The project goal is to operationalize this working, machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. In this project you will:
* Test the project code using linting
* Complete a Dockerfile to containerize this application
* Deploy the containerized application using Docker and make a prediction
* Improve the log statements in the source code for this application
* Configure Kubernetes and create a Kubernetes cluster
* Deploy a container using Kubernetes and make a prediction
* Upload a complete Github repo with CircleCI to indicate that your code has been tested

A detailed project rubric could be found [here](https://review.udacity.com/#!/rubrics/2576/view).

# CircleCI
CircleCI workflow could be found [here](https://circleci.com/gh/pablo-albaladejo/project-ml-microservice-kubernetes)

# Docker
Docker image could be found [here](https://hub.docker.com/r/pabloalbaladejo/project-ml-microservice-kubernetes)

---

## Setup the Environment

* Create a virtualenv and activate it
```
python3 -m venv ~/.devops
source ~/.devops/bin/activate
```

* Run `make install` to install the necessary dependencies

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`

### Uploading the Docker image

To upload the image to Docker Hub: `./upload_docker.sh`

*Note that running this script will prompt for the username and password of the Docker account.*

### Kubernetes Steps

* Setup and Configure Docker locally
* Setup and Configure Kubernetes locally 
    - `minikube start` to start a local cluster
    - `kubectl config view` to check that the cluster has been started (there should be least one cluster with a certificate-authority and server)
* Create Flask app in Container and run via kubectl `./run_kubernetes.sh`

* After you’re are done deploying the containerized application and making test predictions via Kubernetes cluster, you should clean up your resources and delete the kubernetes cluster with a call to `minikube delete`

### Files

* `output_txt_files/docker_out.txt` containes the prediction returned after running the app with Docker

* `output_txt_files/kubernetes_out.txt` containes the prediction returned after running the app with Kubernetes

* `run_docker.sh` contains the steps to get Docker running the app locally:
    - Build the image and add a descriptive tag
    - Run the app

* `run_kubernetes.sh` contains the steps to get Kubernetes running the app locally:
    - Run the Docker Hub container with kubernetes
    - Forward the container port to a host

* `upload_docker.sh` contains the steps to upload the image to the Docker repository:
    - Authenticate & tag the image
    - Push image to a docker repository