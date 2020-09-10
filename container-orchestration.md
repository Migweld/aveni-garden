# Container Orchestration

## In Brief

A method to encapsulate and automate the provisioning, deployment, monitoring and cleanup of multiple application segments

## How it helps us

Using container orchestration we can automate the process of creating & running distinct services, which may be too long-running or have too large a footprint for Lambda functions. We can couple the cluster to any number of other AWS resources using AWS CloudFormation templates to create a declarative infrastructure, all described and version controlled in code.

## Kubernetes

The most popular project for container orchestration today is Kubernetes. Developed by Google, it is available on multiple providers, including AWS

### Kubernetes architecture

Kubernetes consists of a number of components that make up a cluster

<details>
<summary>Click to see the different components</summary>

- Nodes:

  - The bare metal or VPS server, which we are running our services on.

- Pod: The smallest unit of a k8s cluster

  - Provides and abstraction layer over the container
  - Usually runs with one application container per Pod
  - Pods are ephemeral, they will be destroyed and remade depending on resources and state
  - Each pod gets its own IP address. When they die they are assigned a new one

- Service

  - Provides a permanent IP address for pods within the cluster
  - Can be external or internal types depending on what kind of access we want to allow
  - External services types are known as Ingress types, which allow routing to services with things like SSL and domain to IP mapping

- ConfigMap

  - Config maps allow for storage of things like service URLs and names
  - These maps are attached to pods to allow them to access the data within
  - For example, we have a db service with the name 'postgres-db' and a Node application. We can store that db name within the ConfigMap, attach it to the Node pod and use it from there without baking the name or connection string of the DB into our Node application.
  - Credential data, which needs to be secure, can be stored in special type of ConfigMap called a Secret

- Volume

  - Volumes attach to pods to allow persistent storage of data
  - Because pods are ephemeral, if we were to store something in the filesystem of the pod and the pod were to be destroyed, that data would not be persisted.
  - To make sure we can keep that data, we create mountable volumes within our cluster. These point to local or external storage (in AWS terms, this might be an EBS/EFS/S3 instance)

- Deployment

  - Deployments are blueprints that indicate how a Pod should be created, including it's application image, services and any ConfigMaps or secrets attached to it.
  - This allows us to construct replicas of pods in an automatic and predictable way.
  - For example, if we have a Deployment with a Node application, accessible via an Ingress service and connected to a DB service, we can replicate this blueprint across Nodes.
  - The Deployment configuration dictates how many replicas we want at any given time and how they should be updated. This means we can configure it in such a way that we have zero-downtime deployments as well as automated spinning up of containers to deal with load or cover crashes.

- StatefulSets

  - These act like deployments but for stateful applications, like database containers.
  - They allow replication but also ensure that state read/write actions are synchronised, so we don't end up with data inconsistencies when replicating or destroying stateful pods.

  </details>
