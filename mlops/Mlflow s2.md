# MLOps Notes (Sessional 2) (transcription)

Auto-transcribed from `Mlflow s2.pdf` (OCR + AI correction). Diagrams/tables are approximate.

## Page 1
```text
```

## Page 2
### MLOPs
```text
MLOPs
```

## Page 3
### CI/CD pipeline
```text
dependencies
→ virtual env , readme
, makefile
→ git hub actions - yml files
→
Azure
MLOPs (Machine learning + Devops)
Goal: Automate lifecycle of ML models ( training to deployment )
Benefits:
Scalability, Automation : Faster Delivery
monitoring
* CI/CD pipeline
L 3 stages — 1. Build : code, train model, package dependency
Code merged & tested
Continuous integration
2. Test :
Unit test , data validation , model evaluation
automatically
3. Deploy :
deploy model as API , monitor performance
Continuous delivery: deploy changes to production
```

## Page 4
### Dockers
```text
img
container
blueprint defining what
- running instance
inside container using
Dockerfile - static
- Dynamic - run, stop, delete
Dockers. lightweight than VMs
decouples dependency on machines
o hypervisor?
virtual
hardware
hardware
VM OS
App
Host OS kernel
Dockers
More secure than
share Host OS
kernel
Main components
1) Docker Client : CLI to interact with Docker
AWS - Elastic Container Service - Run containers   2) Docker Daemon (Server): Runs in background
3) Image
builds/manages containers
Storage - S3 bucket
4) Containers
5) Docker Registry - Stores Docker
images
AZURE → cont
Azure container Instances
complete package = RAM hungry
Docker server
Docker Desktop
vs LINUX CLI client
(extension) → Container Tools
```

## Page 5
#### Docker commands
```text
run
package on disk
client service
$ docker run hello-world
... can't find locally
a repo in your
PC
pulling from Library,
global =
library = Dockerhub
execution of image
$ docker images
// shows local images
$ docker search
busybox
// searches Hub,
$
//
pull
busybox
"  "
run
busybox::latest
by default.
"
run
busybox echo
"Hello from busybox"
"
ps
// shows running containers
each container
"
rmi
image name // Delete image
- unique ID
rm
container-id
img vs container
"
// Delete container
blueprint of package
container
running instance
then created
→ Run busybox - 3 times  3 instances made
once container started you can change its state
stop
pause - suspend
$ docker run -it busybox sh   // sh, bash etc
restarted → run
Interactive mode
you can interact, run commands directly on container
to make changes, then recreate image with these
changes
```

## Page 6
#### Making Docker Image
```text
Docker
image: blueprint   container: running instance
File : script with instruction to build file
Hub : stores imgs
remove.
$ docker container prune
// stops all containers
Tuesday 9th sep
Making Docker Image
1. $ touch Dockerfile
# Base Image — lowest level (os)
you build upon the base image
From python 3.12
docker build -t flask-app
# set working Directory
docker run -p 5000:5000 flask-app
WORKDIR /app
docker push username/flask-app:latest
COPY requirements.txt requirements.txt   RUN pip install -r requirements.txt
layer.
Benefits:
1° caching: if nothing changes in a layer
# copy all source code
COPY ..
Docker reuses it
# Expose Flask Port   Expose 5000 Port
2° smaller images :
only changed layer rebuilt
eg if you change
app.py, the pip install
# Run
Port mapping
won't run as layer cached
CMD["python", "app.py"]
eg Flask runs on 5000
Connect inside container port with host machine
without port mapping app inside
is isolated, can't be accessed by outside
Q) Build github workflow that builds image from your Python app
and pushes to Docker Hub
jobs: build:
runs-on: ubuntu
- name: Push image
steps: checkout code
run : docker push...
- name: Login To Docker Hub
uses : docker/login-action@v2
with:
username: ${{ secret }}
password: ${{ secret }}
- name : Build image
run : docker build -t username/flaskapp
```

## Page 7
#### Volumes
#### Networks
```text
Thursday
Docker
Volumes → Persistent storage for containers
container
mongodb
img
Instead of losing storage when container deleted
changes made
in container
but image same
it maps operations in the container
if crash, new
outside it:
container loses data
$ /, /lib/docker
useful for databases, logfiles, temp data
volume will pointed
to this location
$ Docker Volume
$docker volume ls
$ '' volume create vol_name
// create
// remove
$
volume rm myvol-name
Networks
Docker creates private Virtual Network
each has own IP
Container
Docker service that merges
Exposed ports are only within VN
the IP of each
container
VN
$ Docker Network LS   // show all networks
A: B/mongoDB
A
translated by network into IP
container
```

## Page 8
### Docker-Compose
```text
Docker-Compose
tool to
running
manage
centralizes
multi container
e.g instead of running all containers with long command
web:
img
- docker-compose.yml -
version: '3.x'
services:
web:
img : flask-web
// use prebuilt image
container-name : web-latest
// map port
- 27017:27017
Volumes:
- web-data:/data/db
path of volume
mongo:
img : build: .
// build from dockerfile in current directory
ports:
depends-on: - mongo   // start mongo before image
Run command
build docker-compose up --build
depends-on:
or healthy
--build
ensures image
rebuilt if Dockerfile
- web :
changes
condition : service_started
Stop containers: docker compose down
docker compose up -d   detached mode
```

## Page 9
### Branching
#### Github actions
```text
Sessional
* Branching   $ git clone "www.repolink"
$ cd flask-app
$ git checkout -b new_branch
$ git add .
$ git commit -m ""
$ git push origin new-branch
open pull request   L github → "Pull request" → "New Pull req"
2- compare:
Base Branch → main
compare branch-1 new-branch
3- Request review → merge only when test passed
CI : auto build, test code whenever pushed
change
Github actions : for ci
repo structure :
Flask-app/
— app.py
— requirements.txt
— tests/
L test-app.py
.github/
workflows/
L ci.yml
Rules: • Indentation matters
yml language
L no tab, 2 spaces per level
o Key: value pairs
L eg name: ci pipeline.
o List use [-]
use | multiline command
L
branches:
- feature
- main
o Strings dont need "" unless special character
eg (python-version : 3.10, message: "Helloworld")
```

## Page 10
#### ci.yml main components
```text
Main
components:
ci.yml
- Jobs: group of steps
name: CI pipeline
# name of workflow
on:   # event trigger
push:
when to trigger
workflow if
code pushed
branches:
run
if code
- main
to branch
- features/*
Github hosted   Self hosted
pull_request:
branches:
collection of
jobs:
steps that
build-and-test:
on same environment
runs-on: ubuntu-latest
# running envir
steps:
# step seq
checkout code
- name : Checkout code
2 types
custom
prebuilt
shell
(uses:)
command
(run)
uses : actions/checkout@v3
- name : setup python
uses : actions/setup-python@v4
with:
# 'with' when action require parameters
python-version : "3.10"
- name : Install dependencies
run : |  multiline
python -m pip install --upgrade
pip install -r requirements.txt
- name : Run tests
run : pytest
```

## Page 11
#### Summary
```text
Summary
Name:
name of action it will show
on:
pull-req:
PR
list of branch
push:
build_and_test:
runs_on: ____
steps:
- name:
uses: prebuilt.
or run:
with:
Q) Write Yaml code that runs tests parallel across ubuntu & windows
name: Parallel Test
on :
push:
branches: - main
jobs:
tests:
runs-on: ${{ matrix.os }}
To run multiple
strategy:
OS
matrix:
os : [ ubuntu-latest, windows-latest ]
steps:
- name: checkout code
- uses: actions/checkout@v3
- name: Run tests
run : echo "Running tests on ${{ matrix.os }}"
```

## Page 12
### Deployment to Azure with Github Actions
```text
Deployment to Azure with Github Actions
Steps :  1- Azure portal → create new AppService → Web App
o runtime stack: Python 3.10
o nearest region
o OS: Linux   Note: App-Name
2- Configure Deployment Credentials
eg webapp → Deployment Centre → Select Git Action as CI/CD
authorize Github
3- Add Azure Publish profile to Github secrets
4- Create deploy workflow
name: ...
on: ...
job: ...
steps
ubuntu
steps:
- checkout code
- setup python
- install dependencies
- run test    Steps: - name: Deploy to Azure
uses: azure/webapps-deploy@v2
with:
app-name: flask-demo-1245   publish-profile : ${{ secret }}   package: .
```

## Page 13
### Jenkins
#### Pipeline
#### Parameters
```text
same purpose as Git Actions but more flexible
self hostable
large plugin ecosystem
Jenkins
automation server for CI/CD
allows devs to auto build/test/deploy
Pipelines written in Jenkinsfile using groovy scripts
* Pipeline defines steps to build test deploy
pipeline {   agent any
// run on any available jenkins agent
agents runs the pipeline on VM
stages: logical steps
stage('build'){
steps{   echo 'building proj'
}
stage('Test'){
stage('Deploy'){ ... }
}
control pipeline at runtime eg many branches, instead of hardcode ask user which branch to build
Parameters:  pipeline {
agent any
parameters{
default val
string(name: "Branch", description: "Git branch to build")
stage('Deploy'){
booleanParam(name: 'RUN_TESTS', default Value: true, description:
choice(name: 'ENV', choices: ['dev','stage','prod'], desc...
steps{
echo "Deploy to: ${params.ENV}"
}
steps{
echo "checking out branch : ${params.BRANCH}"
git branch:"${params.Branch}", url:"gitrepo"
stage('Test'){
when {
expression {params.RUN_TESTS}
}
steps{
echo 'Running tests'
```

## Page 14
### Kubernetes
#### Architecture
```text
Kubernetes
official container orchestration (docker compose same thing)
by google
needed in microservices has 100's of containers so docker compose
not enough
High availability
scalability
security
easy management
→ Disaster Recovery ( backup & restore)
* Architecture
master node
(control plane)
worker node
#2
#3
containers
worker node
each node has multiple container
Kubelet Service
→ communication
→ CPU usage
→ memory
→ process
→ traffic
```

## Page 15
#### Master Node
#### API server
```text
Master Node
→ doesn't run tasks
→ entry point to your K8s cluster
API server
→ controller manager (CM)
→ scheduler
L ensures pods placement
→ 'ETCD'
K8s backup store
Master Node components: ① API server
② controller manager
③ scheduler  ④ ETCD
To make API server you need
1, UI   2, CLI   3, API
master → low resource
Virtual machine
worker → higher
```

## Page 16
#### Pod
```text
local cluster try minikube
Pod
smallest unit in K8s
Abstraction over container
usually 1 application per pod
each pod own IP address
```

## Page 17
### Hidden Technical Debt ML systems
#### Maturity Level
```text
Skipped
view Paper:
Hidden Technical Debt ML systems
Maturity Level
ML
Model
Data
Training
Preprocess
extraction
Model
Evaluation
model trained
model
Deploy
Differences in ML vs Traditional software
→ Data changes
- monitoring
→ Performance monitoring
→ monitoring
Accuracy
Predictive
Power
No of users, latency
```

## Page 18
#### Manual
#### Level 1
```text
Manual T1
→ Data Prep
→ No versioning
→ pipeline jungle, data dependencies, entanglement
→ ML engineers communicate with ops through trained models
levels:   ML  |  OPs
model serving
Trained Model
Prediction Service
model
registry
Level 1 :
Data Analysis
Model Analysis
Data valid
Data prep
Training   eval   validation
Feature
Store
Hack A
Source
code
ML
OP
Pipeline
Deployment
block
A
Source
Repo
Data
Automated
pipeline
New versioning available
ML meta Data
Co-deployment
core
```

## Page 19
### Kubernetes CKS
```text
Kubernetes CKS
L Fireship
managing containerized workloads in cloud
e.g Kubernetes for binance - market cloud
- market open → scale containers
L replace container if one fail
A system deployed on Kubernetes is called a Cluster
Brain of operation is the control plane which exposes a api server
which can handle internal
also contains a Key/value database
external req to manage cluster
called ETCD - store info about running
the cluster or persistent state
Scheduler
Kubelet
etcd
Api
IP
node
node
node
control plane
→ control plane manages worker machines called nodes
→ each Node runs a Kubelet
tiny application to communicate back with the main
control plane mothership
→ each node contains multiple Pods
smaller deployable unit in K8s
group of containers / 1 or more
Node
Pod
provides shared storage/network for containers
- machine
pods ephemeral = dies/respawn new IP   each pod has own IP address
where containers
run
```

## Page 20
#### Pods and Services
#### Deployment
```text
Pods
→ Pod dies/respawn new IP to be created so
Service used
internal
external
lifecycle of Pod, service not connected
within
outside. Ingress
eg K8 Cluster
service is https://124.89.10.12:8080
eg
Ingress
Pod A → runs redis
Minikube: lets you locally test K8 component
Pod B → runs nginx
inside a single-node cluster.
on your machine
Pod C → runs backend app
Pod D → runs database
Node 3 (control/master)
→ workload increases then K8 increase
no of
Nodes 2
L also takes care of
- networking
- secret management
→ K8 is designed for High Availability
- persistent storage ..
L way it
achieves by maintaining
replica set:
→ You describe Objects in yaml
L: set of running pods ready to go at any time
define state of cluster
In K8 to run an app eg Flask you need
Service
apiVersion: apps/v1
Deployment
Kind: Deployment
— service manages networking & exposes app
metadata:
- Depl : manages pods & ensures app is running
name: nginx-deployment
spec:
deployment ...
replicas: 3
// describe behavior in spec field
pods with the same
label
containers:
- name : nginx-flaskapp
apiVersion: v1
image : nginx:1.14.2
Kind: service
metadata:
- containerPort : 80
spec:
links service to pods
unique
name: flaskapp-service   name for service
selector: labeled flaskapp
app: flaskapp
- name: cool-volume
ports:
- port: 8080
Q1, why flaskapp not accessible in minikube?
Target port: 8080
Problem: You deployed service as Load balancer, expecting external IP
type: LoadBalancer requests external IP to allow users
Reality: minikube is local so doesn't give external IP
solution: use minikube to expose service locally
minikube service flaskapp-service
```

## Page 21
### Configmap
### Secrets
### Volume
```text
configmap
if pod changed the endpoint for communication b/w pods change
and thus
you have to rebuild the image, make pod
service
solution: configmap
outside of image just create new pod's name
with endpoint
DB-url = mongo-db-service
endpoint
pod-name
Secrets
alike configmap but it user, password of a database
new pod = diff user, password so use secret to store these
stored in base64
use 3rd party encryption for further security
Volume
stores persistent data
local
outside of pod
remotely
referenced to
the storage
```

## Page 22
### Deployment
```text
abstraction above pods
if pod dies substitute with replica
deployment config file, ( prev page)
metadata:
spec:
status:
//running status etc.
Problem: we cant replicate DB pod to ensure data consistency
so use statefulset
eg App called coinchange
Flask-coinchange-app/
Dockerfile
requirements.txt
deployment.yml # how to run app eg (image, replicas)
service.yml # how to expose app (Type, selector, Port)
then pods re-service
readme.md
LoadBalancer (external)
shared route app visibility
ClusterIP (internal)
NodePort (internal)
```

## Page 23
### DVC (data versioning control)
```text
DVC
data versioning control
git cant store large dataset, model in ML
so we use dvc (tool) to track this
dvc tracks real dataset/model
git tracks metadata files of dataset/model
git + dvc used in collaboration
Links to an external drive ( Gdrive, S3
Base project
Example workflow
1) git init // makes .git folder
ml-project/
data/
// makes .dvc folder
dvc init
train.csv
model/
#Track dataset
L r
2) dvc add data/train.csv // track dataset
src/
metadata file appears → train.csv.dvc
preprocessing.py
L data/
train.csv
train.py
train.csv.dvc
Data copied to .dvc/cache
git add data/train.csv.dvc .gitignore
readme.md
runmodel.py
git commit
dvc config core.autostage true //automatically track file change
L auto adds, runs dvc add
```

## Page 24
#### Tracking changes
#### Go back to previous data
#### Remote storage setup
```text
Tracking changes
1. change data : a script like get-data.py changes data
2. check status :
Git doesn't find changes
but dvc does dvc status
3. Add change to dvc dvc add data.csv
4. Git with note #data.csv.dvc has changed add it
5. Commit
Go back to previous data
dvc logs // find prev version
git checkout
dvc checkout
Remote storage setup
Add remote: dvc remote add g-drive-remote gdrive:// (folder-val)
This command changes config file so git add, commit
do get client-ID, secret from google
dvc pull
```

## Page 25
### Automation: Dvc pipeline
#### Automate commits or CI/CD using Github Actions
```text
file automate
get data, preprocess, train
Automation: Dvc pipeline , dvc.yml
dvc → used to automate pipeline to retrain model - when new data coming
dvc repro // reruns pipeline
dvc metrics show
dvc params show
dvc metrics diff // show differences in metrics
How it knows to rerun
dvc.yml eg
stages:
dvc checks
get-data:
cmd: python src/get-data.py
2- datafile (outs)
deps: - src/get-data.py
3- parameters ( params.yml)
for changes
outs:
if found
- data/raw.csv
dvc repro
preprocess:
train: ...
Automate commits or CI/CD using Github Actions
1- Run dvc repro
2- Add updated files
3-
commit, push
create .github/workflows/auto-train.yml file
```

## Page 26
```text
name : Auto train pipeline
on :
push:
branches:
- main
pull request :
jobs :
steps:
- name: set-up python
uses: actions/setup-python
with:
python-version: 3.10
- name: Install dependencies
run: pip install requirements.txt
- name: Pull data
run: dvc pull --force
- name : rerun pipeline
run: dvc repro
```

## Page 27
### Mlflow
#### Components
#### Tracking
```text
Mlflow
tool lib in python to manage ML experiment
helps in
• Tracks experiments
performance score (e.g accuracy)
• Reproduce training runs anywhere
• Save/ Load models easily
files, plots, save models
• version & manage models
Components  Purpose
e.g
log experiments (parameter, metric, artifacts)
compare model / tuning results
Tracking
Run training code anywhere
Projects
Package code so can run anywhere
models
Save models in standard format
deploy model anywhere
Model Registry  version Manage models
promote best model to production
1 Tracking
import mlflow
Workflow
1- install mlflow
import mlflow, sklearn
2- import mlflow
with mlflow.start_run():
3. initialize (set experiment)
mlflow.log_param("learning_rate", 0.01)
3. train model & record
4. start run
• Log-metric
• Log-artifact
mlflow.sklearn.log_model (model)
$ mlflow ui // start mlflow ui, goto localhost:5000
mlflow.autolog() // autodetects model & logs every param
tip: hyper parameter tuning using gridsearch
method to auto test multiple combinations of parameters
to find best
L you give model
- dictionary of parameters
it returns
best model + best parameter
grid = GridSearchCV(model, param_grid, cv=3, ...)
```

## Page 28
#### Projects
#### Models
```text
requires Git repo
This file
2) Projects
create MLproject file
name: my-ML-project
conda-env: conda.yml
entry points:
main:
parameters:
n_estimators: {type: int, default: 100}
max-depth: ...
command: "python train.py --n-estimators {n-estimators} ..."
function that can be run
optional: conda.yml file for dependency
Running the project
$ mlflow run . // default param
$ mlflow run . -P n-estimators=200 -P max-depth=8 //
models
3)
MLmodel //metadata.md
when you save a model using mlflow it creates a repo like this
model flavours
conda.yml //dependencies
model.pkl //actual model
pytorch
mlflow.sklearn
scikit-learn
. pytorch
example import mlflow.sklearn
XG-boost
with mlflow.start_run():
model = RandomForest
mlflow.sklearn.log_model (model)
mlflow saves model in standard format so
saved in
can be
loaded into python
mlruns/
<experiment-id>/
used in webapp
<runid>/
deployed as rest API
artifacts/
model/
mlflow models serve -m runs:/<runid>/model -p 1234
serves as API, now send request at localhost : 1234
```

## Page 29
#### Model Registry
```text
4) Model Registry
L Hub of models
track model version (v1, v2...)
Promotes model : Staging → Production
L stores notes, metadata, description
result = mlflow.register_model("runs:/<run-id>/model", "HousePriceModel")
mlflow.transition_model_version_stage(
name = "HouseP..."
version=1
)
stage = "Production"
Demo workflow  1- python tracking.py
2- mlflow run -e tracking --env-manager local
ran
didnt run and
as requires more info
we defined experiment name in tracking.py but didn't tell same name in cmd
so it created another experiment & conflicted with Herane
Add "--experiment-name Basic-Tracking-Demo" at end of
cmd 2
```

## Page 30
### Airflow
#### DAG
#### Operator
#### Task
```text
Airflow
schedule/monitor workflows using DAG
Why Airflow> cron job?
Dynamic: Workflows defined in python, allow conditional logic, loops, parameters
Dependency management : correct order
Monitoring & alerting : web UI
retries & errors
extensible: can add own operator + libraries
DAG? => directed acyclic graph : collection of tasks with directional dependencies
No circular dep
Operator?
defines a single task type (what kind of action performed).
from airflow.operators.python import PythonOperator
1- PythonOperator
2- Bash operator
def greet():
3- EmailOp..
print("Hello world")
4- Branch
task? = instantiated operator
task = PythonOperator( // constructor with parameters
task_id = 'sayhello' // name
python-callable = greet // which func to call
task2 = BashOperator(
taskid =''
bash_command = """
cd /tmp
"""
task3 = EmailOp.. (
taskid
to = "
gmail.com"
subject= 'Daily Report - {{ ds }}'
html_content = """ <h3> Report </h3>
)  <p> .... </p> """
```

## Page 31
#### Weather ETL
#### Branch Operator
#### Taskflow API
```text
Weather ETL extract transform load
decorator
Branch Operator
default-args=
BranchOP
schedule-interval = @daily
import
start-date=.
tags = ['weather', 'postgres']
from airflow.operator.python ^
def choose_branch( context):
def weather_pipeline(
@taskgroup(groupid='extract-group')
if hour<12
def extract-group():
return morning task
else
@task(
taskid ='extract_weatherdata'
retries =3
branch = BranchPythonOperator(
def extract_weather_data():
taskid:
python-callable = choose Branch
response = requests.get(url, params)
except request-exception
logging.error ('Error fetching')
raise
return data
def @taskgroup( transform)
Define all task+groups
extracted data = extract_group()
Define dependencies
transform-data = transform-group()
dag = weatherpipeline() { // instantiate Dag
Taskflow Api
No operators as @task becomes python function
Xcoms are automatic
pushed
cross communication
any return value from @task func is pushed as Xcom
```
