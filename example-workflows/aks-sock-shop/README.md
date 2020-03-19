# Deploy Sock Shop demo to Azure Kubernetes Service (AKS)       

This sample workflow deploys the [Weavework's Sock Shop demo](https://microservices-demo.github.io/) to the [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/en-us/services/kubernetes-service/).
The workflow first provisions a Azure Resource Group, then deploys an AKS cluster into the Resource Group. 
Next, the workflow creates a namespace on top of the AKS cluster and then deploys the Sock Shop demo into it. 
Finally, the workflow provides a Slack notification and then outputs the URL of the Sock Shop demo. 

## Prerequisites

Before you run the workflow, make sure you have access to the following:
- A Slack authentication token. For more information, see [Getting a Slack token](https://get.slack.help/hc/en-us/articles/215770388-Create-and-regenerate-API-tokens). 
- Azure account and service principal 
  > For more information on creating a service principal, see [Create an Azure service principal with Azure CLI](https://docs.microsoft.com/en-us/cli/azure/create-an-azure-service-principal-azure-cli?view=azure-cli-latest).

## Run the workflow

Follow these steps to run the workflow:
1. Add your Slack authentication token to the workflow as a secret.
   1. Click **Edit** > **Secrets**.
   2. Click **Define new secret** and use the following values:
      - **KEY**: `slacktoken`
      - **VALUE**: Enter your Slack authentication token
2. Add your Azure service principal credentials as a secret.
   1. Click **Edit** > **Secrets**.
   2. Click **Define new secret** and use the following values:
      - **KEY**: `tenantid`
      - **VALUE**: Enter your Azure tenant_id associated with the service principal
      - **KEY**: `username`
      - **VALUE**: Enter your Azure username associated with the service principal
      - **KEY**: `password`
      - **VALUE**: Enter your Azure password associated with the service principal
3. Configure your workflow parameters.
   1. Click **Run** and enter the following parameters:
      - **location**: Enter the name of the Azure location to deploy to. 
      - **resourcegroupname**: Enter the name of the Resource Group you'd like to create and deploy the cluster to.
      - **slack_channel**: Enter the name of the Slack channel you'd like to
        notify when the workflow completes. For example, `#nebula-workflows`.
      - **slack_message**: Enter a message for the Slack notification. For
        example, `K8s cluster successfully provisioned with Nebula!`
4. Click **Run workflow** and wait for the workflow run page to appear. 

## Open the Sock Shop site in a browser

To find the URL for your Sock Shop site:
1. Select the `output-url` step within the `Logs` view of the workflow 
2. Copy the output and paste the URL into a browser. Make sure protocol is `http` and not `https`.

Congratulations! You've deployed the Sock Shop demo to AKS.

**Useful topics:**

- For more information on our curated step specifications, see [Step specifications](../step-specifications.md).
- If your team uses Microsoft teams, try the [Microsoft Teams notification](../step-specifications/msteams-notification.md) step.

<p align="center"><img src="./aks-sock-shop.png"></p>