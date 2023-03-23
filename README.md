# workstation

```
docker run --rm -it \
    -v ${PWD}:/work \
    -v ${HOME}/.kube:/root/.kube \
    -v /var/run/docker.sock:/var/run/docker.sock \
    tuanonehour/workspace:1.2
```