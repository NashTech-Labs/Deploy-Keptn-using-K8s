# TechHub2-DeployKeptnUsingKeptn

## Pre-Requisites:
Kubctl with atleast one node should be present. OR Minikube should be installed.

## Workings steps to Deploy Keptn with Replication Controller:

- Deploy keptn rc with (default 3 replicas) following command.
```
kubectl create -f keptn-rc.yaml
```

- Get output of running pods using this command.
```
kubectl get po -o wide
```

- Scale Up / Scale Down the pods using this command.
```
kubectl scale rc keptn-rc --replicas=5
kubectl scale rc keptn-rc --replicas=1
```

- Delete keptn-rc after deployment
```
kubectl delete -f keptn-rc.yaml
```
**Note** Also there is a file main.sh that does all the above steps for you :)

### Executions steps
Just execute the main.sh file using this command. Rest script will handle everything relaxed

```
bash main.sh
```

## Flow of Deployment:
```mermaid
flowchart TD
    A[main.sh executed!!];
    A --> B[Enter Number of pods to create for Keptn];
    B --> C[Enter Count];
    C --> D[Keptn deployed];
    D --> E{Do you want to scale up Pods?};
    E -- Yes --> F[Enter number of pods to scale up];
    F --> G[Pods have been scaled up!]
    E -- No --> H{Do you want to scaldown Pods?};
    G --> H{Do you want to scaldown Pods?};
    H -- Yes --> I[Enter number of pods to scale down to];
    I --> J[Pods have been scaled down!];
    H -- No --> K{Do you want to delete this Deployment?};
    K -- Yes --> L[Deployment Deleted];
    K -- No --> Z[Quit the script!];
```