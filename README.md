# Kubernetes Resources Overview

This document provides an overview of various Kubernetes resources, including deployment types, services, file injection methods, and configurations.

## Table of Contents

1. [Deployments](#deployments)
   - [StatefulSet](#statefulset)
   - [DaemonSet](#daemonset)
   - [Job](#job)
   - [CronJob](#cronjob)
   - [Pod Init-Container](#pod-init-container)
   - [Horizontal Pod Autoscaler](#horizontal-pod-autoscaler)
   
2. [Services](#services)
   - [ClusterIP](#clusterip)
   - [NodePort](#nodeport)
   - [LoadBalancer](#loadbalancer)
   - [Ingress](#ingress)

3. [Injecting Files into Pods](#injecting-files-into-pods)
   - [ConfigMaps](#configmaps)
   - [Secrets](#secrets)

---

## Deployments

### StatefulSet

- **Definition**: A StatefulSet is a Kubernetes resource designed to manage stateful applications. It provides guarantees about the ordering and uniqueness of pods.
- **Use Case**: Best for databases or applications where identity and storage are important (e.g., Cassandra, Zookeeper).

### DaemonSet

- **Definition**: A DaemonSet ensures that a copy of a specific pod runs on all (or a subset of) nodes in the cluster.
- **Use Case**: Useful for logging, monitoring agents, or any application that needs to run on every node.

### Job

- **Definition**: A Job creates one or more pods and ensures that a specified number of them successfully terminate.
- **Use Case**: Ideal for batch processing tasks like data migration or report generation.

### CronJob

- **Definition**: A CronJob schedules jobs to run at specific times or intervals, similar to cron in Unix/Linux.
- **Use Case**: Useful for regular maintenance tasks, backups, or scheduled reporting.

### Pod Init-Container

- **Definition**: Init containers are specialized containers that run before app containers in a pod. They can contain utilities or scripts for setup.
- **Use Case**: Great for initialization tasks, such as waiting for a service to be available or setting up configurations.

### Horizontal Pod Autoscaler

- **Definition**: This resource automatically scales the number of pod replicas based on observed CPU utilization or other select metrics.
- **Use Case**: Ensures that your application can handle varying loads without manual intervention.

---

## Services

### ClusterIP

- **Definition**: A ClusterIP service is the default type, which exposes the service on a cluster-internal IP. It can only be accessed from within the cluster.
- **Use Case**: Ideal for internal communication between services.

### NodePort

- **Definition**: A NodePort service exposes the service on each node’s IP at a static port. You can access it externally via `<NodeIP>:<NodePort>`.
- **Use Case**: Suitable for exposing services to external traffic without needing a load balancer.

### LoadBalancer

- **Definition**: A LoadBalancer service creates an external load balancer in the cloud provider (if supported) and assigns a fixed, external IP address.
- **Use Case**: Best for applications that need to be accessed from the internet with automatic load balancing.

### Ingress

- **Definition**: Ingress manages external access to the services within a cluster, typically HTTP. It provides routing rules to manage traffic.
- **Use Case**: Useful for exposing multiple services under a single IP address with path-based routing.

---

## Injecting Files into Pods

### ConfigMaps

- **Definition**: ConfigMaps are used to store non-sensitive configuration data in key-value pairs. They can be injected into pods as environment variables or mounted as files.
- **Use Case**: Ideal for configuration settings that are not sensitive and need to be easily updated.

### Secrets

- **Definition**: Secrets store sensitive data, such as passwords, OAuth tokens, and SSH keys, in a base64-encoded format. They can be used as environment variables or mounted as files.
- **Use Case**: Essential for managing sensitive information securely within applications.

---

## Conclusion

This document serves as a high-level overview of essential Kubernetes resources used for managing applications effectively. Understanding these concepts is crucial for building scalable and resilient applications on Kubernetes.

