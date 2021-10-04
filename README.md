# REFERENCES

Retrieved from https://github.com/jbkarle/postgrest

## POSTGREST PROJECT


### BUILD AND UPLOAD IMAGES

```
docker build . -t postgrest:0.0.1
gcloud builds submit --tag gcr.io/bitnami-cluster-327717/postgrest/postgrest:latest
```

### SETUP GKE 

Enable `container.googleapis.com` in project `https://console.cloud.google.com/apis/ SETUPlibrary/container.googleapis.com?authuser=1&project=gbucket-on-gke`

```
gcloud container clusters create bitnami-gke-cluster --num-nodes 1 --zone europe-west1
```

### ACCESS

Assuming you have downloaded the keys for the project

```
gloud auth login
gcloud config set project bitnami-cluster-327717
gcloud container clusters get-credentials bitnami-gke-cluster

```


### HELM

```
helm dependency build
helm install postgrest . 
```
