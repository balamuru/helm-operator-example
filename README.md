# helm-operator-example
A simple tutorial on how to create a Kubernetes Helm Operator ie. a Kubernetes Operator from a Helm Chart

## What is a Helm Chart
A means of packaging up a collection of K8s specifications (such as yaml files) in a managed idempotent fashion.  For example, a simple Helm Chart may contain deployment.yaml a service.yaml files with placeholders for number of replicas, name etc. 

## What is an Operator
By default, K8s comes with several exisiting resource ```Kind``` types. For example, some pre-packed native K8s resources are ```Deployment``` and ```Service```. Basically, the contents of the ```Kind``` field in yaml spec. An operator is an example of a Custom ```Kind``` a.k.a. **Custom Resource Definition (CRD)** called what ever you want eg Foo, Bar, MyKind ... You get the idea.

## What is a Helm Operator
A Helm Operator takes an existing Helm Chart as input and  magicallly creates a CRD (say MyKind) out of it (that will need to be installed on the target K8s cluster). Then, the CRD can be operated upon as a first class K8s citizen eg ```kubectl create MyKind abcd```

## Benefits of creating a Helm Operator
* First Class K8s Citizen
* Can be managed using kubectl commands
* Multiple instances of a CRD can be created in a cluster(as opposed to a single instance for Helm Chart(

## Exammple
### Create a sample Helm Chart
```
helm create nginx-app
helm package nginx-app
```

