
![](https://dt-cdn.net/images/dynatrace-logo-rgb-cph-800x142px-ac1b21b785.svg)

# Dynatrace Oneagent Helm Chart
This helm chart is designed to facilitate the deployment of the Dynatrace OneAgent as a Helm Chart.

### Prerequisites
1. A Dynatrace namespace has been created in your cluster
2. The Tiller Service Account has access to the Dynatrace namespace
3. The Dynatrace Operator has been succesfully deployed to your cluster

**Please note, you MUST install the OneAgent Operator to your cluster BEFORE deploying the OneAgent.**
#### Dynatrace Operator Helm Chart:
<https://github.com/kyledharrington/dynatrace-operator>

### Notes
- This chart was built & tested using Helm v2.16.1. This has not been tested with Helm v3
- The OneAgent pods in this chart are deployed with a Custom Resource Definition which is created when the Operator is deployed
- The Dynatrace Operator MUST be succesfully deployed prior to deploying the OneAgent
- The core Dynatrace Kubernetes installation instructions can be found below and should be used for reference for any custom neededs (ex. taints, tolerations, docker image location) 

### Deploy OneAgent on Kubernetes (Dynatrace Documentation)
<https://www.dynatrace.com/support/help/infrastructure/containers/how-do-i-deploy-dynatrace-oneagent-on-kubernetes>


## Configuration & Deployment
1. Verify the Dynatrace Operator pod is running before deploying the Dynatrace OneAgent chart
 
2. Update the key/value pairs in the values.yaml file:
- apiUrl: (this is your tenant url)
- apiToken:
- passToken: 
    - Tokens can be generated from the Dynatrace UI by navigating to:
    - **Settings --> integration --> Dynatrace API**

- Please see below for an example for formatting purposes:
![](https://storage.googleapis.com/kdh-github/helm-oneagent/values.png)
 
3. Deploy the OneAgent Helm Chart
```
helm install --name dynatrace-oneagent /path/to/chart
```