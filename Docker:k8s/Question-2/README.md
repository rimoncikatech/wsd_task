# Kubernetes Pod Restart Diagnosis

This repository provides instructions and examples for diagnosing the reason for a pod restart in a Kubernetes cluster, specifically for a project named "internal" in the "production" namespace.

## Prerequisites

- Access to a Kubernetes cluster.
- kubectl installed and configured to interact with your Kubernetes cluster.

## Steps to Identify the Reason for a Pod Restart

### 1. List the Pods in the Namespace

First, list all the pods in the `production` namespace to identify the pod you are interested in.

```bash
kubectl get pods -n production

2. Describe the Pod
Once you have the pod name, use the kubectl describe pod command to get detailed information about the pod, including the reason for the restart.

kubectl describe pod <pod-name> -n production


3. Check Events Section
Look at the "Events" section in the output of the kubectl describe pod command. This section provides detailed information about the events that have occurred, including reasons for pod restarts.

4. Check Container Status
In the kubectl describe pod output, there is a section for each container in the pod that includes information about the container status. Look for Last State and State fields to see why the container restarted.