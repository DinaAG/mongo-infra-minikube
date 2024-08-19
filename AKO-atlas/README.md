# Atlas Kubernetes Operator and Minikube

Get a kubernetes cluster, the MongoDB Atlas Kubernetes Operator and and Atlas Project/Database setup in minimal time/effort

## Requirements
- minikube if you want this script to setup a cluster for you
- An Atlas account (where you will deploy your cluster)
- An Atlas API Key (how the operator talks to Atlas)

## Usage
Simply run this command (from this folder) and follow the prompts:
```
bash quick-start.sh # on linux/mac
powershell quick-start.ps1 # on windows
```

You can then take a look at the generated `deploy-a-cluster.yaml` file, or run:
```
kubectl apply -f deploy-a-cluster.yaml
```

This will create your secret (for your api key), your project, and an m10 deployment. It will also set up a tag with the projectname you provided and a keep.until variable (which we use to automatically remove test clusters) set to tomorrow.

## to restore and create vector search
1. after finishing the above step and made sure that the cluser is reflected successfully in the UI fully deployed.
2. extract the attached mongodump.zip in any location to use later, can be in same folder or in downloads folder for example.
3. run (on mac only for now):
```
bash restore.sh 
```
and add the extracted folder location + MongoDB Atlas connection URI, for example mongodb+srv://<username>:<password>@<cluster-url>/?retryWrites=true&w=majority
4. that's it.

## Clean up
To remove the minikube cluster and any tools that where downloaded to this directory simply run
```
bash clean-up.sh # on linux/mac
powershell clean-up.sh # on windows
```
