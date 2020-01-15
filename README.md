# Study case of KrakenD

Study case of Krankend API Gateway + Docker.

## Dependencies

- Docker

## How to

**Krakend.json** contains the structure to use the Gateway. It was generated [here](https://designer.krakend.io/#!).

```sh
docker run -p 8080:8080 -v $PWD:/etc/krakend/ devopsfaith/krakend run --config /etc/krakend/krakend.json
```

## References

- [KrakenD](https://www.krakend.io)
- [Docker KrakenD](https://github.com/devopsfaith/krakend)
- [KrakenD + Kubernetes](https://www.krakend.io/blog/krakend-on-kubernetes)

