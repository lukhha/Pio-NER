### Mlflow server start steps

mlflow server --host 127.0.0.1 --port 8080


mlflow models serve -m runs:/f768fdf4a48c40b6b5c3c14408e5ecff/model -p 5000 --no-conda


### mlflow local inference




### Deployment Steps

mlflow models build-docker -m runs:/<run_id>/model -n <image_name> --enable-mlserver

mlflow models build-docker -m runs:/1d917a3a56d849c9bf2bf48afc287ba4/model -n mlflow_first --enable-mlserver

mlflow models serve -m runs:/f768fdf4a48c40b6b5c3c14408e5ecff/model -p 5000 --no-conda


### Reference for mlflow build-docker fail

https://github.com/mlflow/mlflow/issues/9259

I had the same issue and thought I found the reason of the issue. When RUN command in the Dockerfile tries to access network to download data it's blocked. Adding --network=host to CLI command fixes the issue.

I first generated the Dockerfile and metadata folder using the following command:

#mlflow models generate-dockerfile -m models:/prova_model/Staging --enable-mlserver

Then I built the image using the following command

#docker build --tag mlflow_ner . --network=host




docker push 'mlflow_dockerfile'

kubectl apply -f kdeploy2.yaml --dry-run=client


### Kdeploy dry run client: 

mlflow models generate-dockerfile -m runs:/e8b2a54edc2c46a4b4f83ec458021a4d/model --enable-mlserver

docker build --tag lukishyadav/mlflow_ner . --network=host

kubectl apply -f kdeploy_ner.yaml







mlflow models build-docker -m runs:/e8b2a54edc2c46a4b4f83ec458021a4d/model -n lukishyadav/mlflow_ner --enable-mlserver
