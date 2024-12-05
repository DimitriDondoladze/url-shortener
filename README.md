# url-shortener
Let's Build It: Url Shortener


## Infrastructure as Code

### Download Azure CLI
https://learn.microsoft.com/en-us/cli/azure/

### Log in into Azure
```bash
az login
```

### Create Resource Group

```bash
az group create --name urlshortener-dev --location germanywestcentral
```

### Deploy Bicep

### What if
```bash
az deployment group what-if --resource-group urlshortener-dev --template-file infrastructure/main.bicep
```

### Deploy
```bash
az deployment group create --resource-group urlshortener-dev --template-file infrastructure/main.bicep
```

### Create User for GH Actions
```bash
az ad sp create-for-rbac --name "GitHub-Actions-SP" \
                         --role contributor \
                         --scopes /subscriptions/9ecb3919-6f66-4ea6-a025-5d5f13d8d197 \
                         --sdk-auth
```

### Apply to Custom Contributor Role
```bash
az ad sp create-for-rbac --name "GitHub-Actions-SP" \
                         --role 'infra_deploy' \
                         --scopes /subscriptions/9ecb3919-6f66-4ea6-a025-5d5f13d8d197 \
                         --sdk-auth
```


#### Configure a federated identity credential on an app
https://learn.microsoft.com/en-gb/entra/workload-id/workload-identity-federation-create-trust?pivots=identity-wif-apps-methods-azp#configure-a-federated-identity-credential-on-an-app


## Get Azure Publish Profile
```bash
az webapp deployment list-publishing-profiles --name api-b76p3hqv3qcba --resource-group urlshortener-dev --xml
```