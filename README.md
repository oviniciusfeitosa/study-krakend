
# Study case of KrakenD

Study case of Krankend API Gateway + Docker + Kubernetes.

## Dependencies

- Docker
- Kubernetes

## How to

**Krakend.json** contains the structure to use the Gateway. It was generated [here](https://designer.krakend.io/#!).


- Install [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-on-linux)

- Install Minikube

```sh
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_1.8.1-0_amd64.deb \
 && sudo dpkg -i minikube_1.8.1-0_amd64.deb
```

- Start a cluster using virtualbox driver

```sh
minikube start --vm-driver=virtualbox
```

- Define virtualbox as default driver for minikube

```sh
minikube config set driver virtualbox
```

- Build fake-api with Docker

```sh
cd backend
eval $(minikube docker-env)
docker build -t fake-api -f Dockerfile .
```

- Build KrakenD image

```sh
# in root folder
docker build -t k8s-krakend:0.0.1 .
```

- Get kubernetes info

```sh
cat ~/.kube/config
```

- The `minikube start` command creates a **kubectl context** called “minikube”. To switch to **minikube** context use the command below.

```sh
# Optional:
# kubectl config delete-context minikube

kubectl config use-context minikube
```

- Deploy the backend API in k8s

```sh
kubectl run fake-api --image=fake-api:latest --port=8080 --image-pull-policy='Never'
```


## References

- [KrakenD](https://www.krakend.io)
- [Docker KrakenD](https://github.com/devopsfaith/krakend)
- [KrakenD + Kubernetes](https://www.krakend.io/blog/krakend-on-kubernetes)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/linux)
- [kubectl](https://kubernetes.io/docs/setup/learning-environment/minikube/#interacting-with-your-cluster)
- [Proxy Issues](https://minikube.sigs.k8s.io/docs/reference/networking/proxy)