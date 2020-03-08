
# Study case of KrakenD

Study case of Krankend API Gateway + Docker + Kubernetes.

## Dependencies

- Docker
- Kubernetes

## How to

**Krakend.json** contains the structure to use the Gateway. It was generated [here](https://designer.krakend.io/#!).

- Install Minikube

```sh
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_1.8.1-0_amd64.deb \
 && sudo dpkg -i minikube_1.8.1-0_amd64.deb
```

- Build fake-api with Docker

```sh
cd backend
eval $(minikube docker-env)
docker build -t fake-api -f Dockerfile .

```

```sh
docker run -p 8080:8080 -v $PWD:/etc/krakend/ devopsfaith/krakend run --config /etc/krakend/krakend.json
```

## References

- [KrakenD](https://www.krakend.io)
- [Docker KrakenD](https://github.com/devopsfaith/krakend)
- [KrakenD + Kubernetes](https://www.krakend.io/blog/krakend-on-kubernetes)
