# MicroK8s Valheim server

Run a Vanleim server in MicroK8s!

With thanks to [cbrgm](https://github.com/cbrgm/valheim-docker) for the container image.

## Prerequisites

This deployment assumes you have `/media/k8s/valheim` created and writable by 
MicroK8s.  If you prefer somewhere else for the persistent volume, you can
modify `deployment.yaml`.

## Deploying

Install [MicroK8s](https://microk8s.io) and enable required add-ons.

```
sudo snap install microk8s --classic
sudo microk8s enable dns ingress storage
```

Clone this repository and `cd` into it.

```
git clone https://github.com/joedborg/microk8s-valheim.git
```

Copy the example secrets file and paste it into the current directory.

```
cp ./examples/secrets.yaml .
```

Set your own values in it and deploy it along with the deployment.

```
microk8s kubectl apply -f ./deployment.yaml -f ./secrets.yaml
```

## Cleaning up

```
microk8s kubectl delete -f ./deployment.yaml -f ./secrets.yaml
```
