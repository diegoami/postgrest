# REFERENCES

Retrieved from https://github.com/jbkarle/postgrest

## POSTGREST PROJECT


### BUILD AND UPLOAD IMAGES

```
docker build . -t postgrest:latest
gcloud artifacts repositories create postgrest --project=gbucket-on-gke --repository-format=docker --location=europe-west1 --description="Postgrest Repository"
gcloud builds submit --tag europe-west1-docker.pkg.dev/gbucket-on-gke/postgrest/postgrest:latest
helm dependency build
```

### SETUP GKE 

Enable `container.googleapis.com` in project `https://console.cloud.google.com/apis/ SETUPlibrary/container.googleapis.com?authuser=1&project=gbucket-on-gke`

```
gcloud container clusters create postgrest-gke --num-nodes 1 --zone europe-west1
```

### ACCESS

Assuming you have downloaded the keys for the project

```
gloud auth login
gcloud services enable artifactregistry.googleapis.com
gcloud auth configure-docker europe-west1-docker.pgk.dev
```


### HELM

```
helm dependencies update
# Update repository image in values.yaml 

