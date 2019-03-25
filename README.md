# Work In Progress (to-do list:)
- [x] Сервіс та докерфайл
- [ ] Скрипти YAML для завантаження в Kubernetes
- [x] Bash скрипт, який інсталює сервіс в MiniKube автоматично
- [ ] Kubernetes Readiness check + Liveness check
- [x] Bash скрипт для локального деплою в minikube (без хмарного реєстру контейнерів)
- [ ] Memory scaling (імітувати задачу, що потребує багато пам'яті і вирішити проблему масштабування у випадку досягнення критичного розміру по використанню пам'яті)

## 1. An application + Dockerfile
You can simply run an application in a single container:

### from Docker Hub:
- run `docker run -d -p 5000:5000 --rm --name ylochman-cloud-infra ylochman/apps-cloud-infra:latest`

### or locally:
- clone this repository: `git clone https://github.com/ylochman/apps-cloud-infra.git`
- run `docker build -t ylochman-hw .`
- run `docker run -d -p 5000:5000 --rm --name ylochman-cloud-infra ylochman-hw`

Then go to `localhost:5000` and follow the instructions. To stop and remove container run:

`docker container stop $(docker container ls -f "name=ylochman-cloud-infra" -q)` .

## 3. & 5. Deploy an application with Minikube
Go to `deploy-kubernetes`

Run `chmod +x ./create-deploy-cloud.sh ./create-deploy-local.sh ./stop-deploy.sh`

To deploy an application from local image run `./create-deploy-local.sh -mb`

To deploy an application from cloud registry run `./create-deploy-cloud.sh -m`

Here: 

- `-m` is to first start minikube
- `-b` is to build docker image locally before runing.

To stop application run `./stop-depoly.sh -m`. Here `-m`is to stop minikube.

## Deploy an application onto a Docker Machine Swarm Cluster
It was done for practicing

Go to `deploy-docker-machine`

Run `chmod +x ./create-deploy.sh ./stop-deploy.sh`

To deploy an application run `./create-deploy.sh`

To stop application run `./stop-deploy.sh`

<!-- ### trash -->
<!-- `docker run -p 5000:5000 -it --rm --entrypoint=/bin/bash ylochman-hw` -->
