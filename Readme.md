- choose a data set form `https://plotly.github.io/datasets/` or github `https://github.com/plotly/datasets/blob/master/diabetes.csv`
- create virtual environment
```sh
python -m venv myenv
myenv\Scripts\activate
Set-ExecutionPolicy -Scope Process -ExectionPolicy Bypass #6:11
myenv\Scripts\activate
pip list
pip install pandas
pip show pandas
pip install -U scikit-learn 
pip show scikit-learn
```
- **joblib** is using for most machine learning models (especially NumPy / scikit-learn models).
- use fast api to lanch the model
```sh
pip install fastapi
pip show fastapi
pip install "uvicorn[standard]"
uvicorn --version
```
- Get column type 
```
col_type = df.dtypes
```
- once main.py using fastapi is created
```sh
uvicorn main:app --reload
```
- create a docker file, allow docker desktop
```sh
docker images
docker ps
docker build -t diabetes-model .
docker run -p 8000:8000 diabetes-model
```
- Stop if the docker is running to push the image to docker hub
```sh
docker login
docker tag diabetes-model dkutti/diabetes-model:latest
docker images
docker push dkutti/diabetes-model:latest
```
- check the version
```sh
docker --version
kind --version
kubectl version --client

Get-ChildItem -Path "$env:LOCALAPPDATA\Microsoft\WinGet\Packages" -Recurse -Filter kind.exe
# set this in enviroment variable
[Environment]::SetEnvironmentVariable(
  "Path",
  [Environment]::GetEnvironmentVariable("Path","User") + ";C:\Users\email\AppData\Local\Microsoft\WinGet\Packages\Kubernetes.kind_Microsoft.Winget.Source_8wekyb3d8bbwe",
  "User"
)
```
- completely close all powershell and vscode
```sh
kind --version
kind get clusters
kind create cluster --name diabetes-demo
kubectl config current-context
kubectl get nodes
```
- Now create `deploy.yml` with the correct image
```
kubectl apply -f deploy.yml
kubectl get pods
kubectl get svc
```
- use port forwarding to access the service
```sh
kubectl port-forward svc/diabetes-api-service 1234:80 --address 0.0.0.0
```
- open the url `http://localhost:1234/docs`
- Check the cluster
```sh
kind get clusters
kind delete cluster --name diabetes-demo
kind get clusters
```
