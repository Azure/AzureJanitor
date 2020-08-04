# AzureJanitor

This repo contains all ther necesaary components needed to deploy and onboard to AzureJanitor. See the Contribution guide for how to use or contribute to this repo.


# Introduction

AzureJanitor is a Serverless Service which enables subscription owners to configure auto-deletion (along with verbose monitoring/alerting) of _stale_ resources to save usage costs. A resource is said to be a _stale_ resource if it is not used and hence, is a waste cost to the organization. Integrate this app with Azure subscriptions and it will take care of the cleanup. The cleanup is based on the age of the resources defined by the sub admin. The resources owner can override the deletion conditions afterwards though.

# Architecture 

AzureJanitor Design can be split into 4 major parts as following:

## 1. Recognizing the _stale_ resources :

### Resource Group Tags 

Before diving into this option of recognizing the stale resources, a major azure resource used for this approach is Azure Policy. Azure policy is a resource which enforces built-in/custom rules capabilities at subscription level.  

Firstly we will be defining an azure policy which will be shared/assigned across all the onboarded subscriptions. The policy will auto-tag any new resource group added to the policy as following: 

Key : CreationDate 

Value : utcNow() 
 
Key : DaysUntilDeletion 

Value : 15  

 
Existing resource groups can be remediated by triggering a remediation task. If the tag exists with a different value it will not be changed.  
 
Example of the Azure Policy  which enables adding above tags on resource groups: https://github.com/stefanrothnet/azure-policy/blob/master/append-date-tag-resource-group/azurepolicy.json 

### Resource Insights

## 2. Auto-Alerting 

## 3. Auto-Deletion

## 4. Onboarding

# Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
