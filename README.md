# pypi

## Prerequisites

Make sure you have installed all of the following prerequisites on your development machine:

1. Docker - [Download & Install Docker ](https://docs.docker.com/engine/install/)
2. Kubernetes Cluster (Local or Remote) 
3. kubectl - [Download & Install Kubectl ](https://kubernetes.io/docs/tasks/tools/) 
4. Docker Registry



## Local docker registry

docker run -d -p 5000:5000 --name registry registry:2

## Cloning The GitHub Repository
````
git clone https://github.com/Akshaya-T/pypi.git
````

This will clone the latest version of the pypi repository to pypi folder.

````
cd pypi
````

## Docker build 

````
# localhost:5000 -> replace it with you container registry and port
docker build -t localhost:5000/pypi-server . 
````


## Docker push 

````
# localhost:5000 -> replace it with you container registry and port
docker push localhost:5000/pypi-server  
````


## Apply kubernetes files in k8s folder  

````
# Make sure to change secret values before apply
kubectl apply -f k8s/              

````


## Port Forward and see the PyPi UI 

````
kubectl port-forward <<pod-id>> 8080:80 --address 0.0.0.0
````


## Upload Package pypiserver using Twine

````
python3 -m twine upload -r local dist/
````

## Use pip client to install and verify the package

````
pip install -i http://pypi:pass@localhost:8080/simple mypackage

````

## dummy line to create pr
