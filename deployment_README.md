### Deployment Steps

mlflow models build-docker -m runs:/<run_id>/model -n <image_name> --enable-mlserver

mlflow models build-docker -m runs:/1d917a3a56d849c9bf2bf48afc287ba4/model -n mlflow_first --enable-mlserver


### Reference for mlflow build-docker fail

https://github.com/mlflow/mlflow/issues/9259

I had the same issue and thought I found the reason of the issue. When RUN command in the Dockerfile tries to access network to download data it's blocked. Adding --network=host to CLI command fixes the issue.

I first generated the Dockerfile and metadata folder using the following command:

mlflow models generate-dockerfile -m models:/prova_model/Staging --enable-mlserver

mlflow models generate-dockerfile -m runs:/1d917a3a56d849c9bf2bf48afc287ba4/model --enable-mlserver

Then I built the image using the following command

docker build --tag 'mlflow_dockerfile' . --network=host


docker push 'mlflow_dockerfile'


### Kdeploy dry run client: 

kubectl apply -f kdeploy2.yaml --dry-run=client





