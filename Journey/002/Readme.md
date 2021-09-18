# Azure Budgets and Cost Management

## Introduction

One of the most common concerns raised when any organization is planning a move to the Cloud is Cost. Unlike Microsoft 365 where you have set costs based on license consumption, there are a number of variables to be considered when moving to any Cloud Provider (be that Azure, AWS or others). 

For example, let’s say we want to put a Virtual Machine in the Cloud. Its sounds easy – if this was on prem, you would provision storage on your SAN, assign CPU and Memory, assign an IP Address, and if required purchase a license for the OS and other additional software that will be running on the Virtual Machine.

All of the above still holds true when creating a Virtual Machine in the Cloud, but there are also other considerations, such as:

-	What Storage Tier will the VM run on (Standard HDD, Standard SSD, Premium SSD)
-	How HA do we need the VM to be (Locally Redundant, Geographically Redundant)
-	Does the VM need to be scalable based on demand/local (Auto Scaling/Scale Sets)

In an on-premise environment, there needs to be an up-front investment (CAPEX) to make that feasible. When running with a Cloud Provider such as Azure, this uses an on-demand model (OPEX). This is where costs can mount. 

There are a number of ways to tackle this. The Azure TCO (Total Cost of Ownership) Calculator gives an estimate of costs of moving infrastructure to the cloud. The important word there is “estimate”.

So you’ve created your VM with all of the settings you need, and the TCO has given you the estimate for what total “should” be on your monthly invoice. Azure Cost Management and Budgets can provide you with forecasting and alerts with real-time analysis of your projected monthly spend. That way, there are no nasty surprises when the invoice arrives!

## Prerequisite

Firstly, let’s create our Azure Account. Browse the Azure Portal to sign up. You get:

-	12 months of free services
-	$200 credit for 30 days
-	25 always free services

Once your account is set up, go to https://portal.azure.com to sign in

## Instructions - the Azure Portal Method

Once you’ve signed in, you can search for “Cost Management and Billing”

![image](https://user-images.githubusercontent.com/80047500/133889582-fb445e25-4bec-47a1-b193-18b5bea5ec97.png)

From the “Cost Management + Billing” page, select “Cost Management” from the menu:

![image](https://user-images.githubusercontent.com/80047500/133889591-4afdd150-40c5-4a9a-9404-433c977f478d.png)

This brings us into the Cost Management Page for our Azure Subscription:

![image](https://user-images.githubusercontent.com/80047500/133889594-869a8b8d-a19a-4afe-b533-ae98c8114c15.png)

One important thing to note here before we go any further. We can see at the top of the screen that the “Scope” for the Cost Management is the Azure Subscription. In Azure, Budgets can be applied to the following:

- Management Group — these allow you to manage multiple subscriptions
- Subscriptions — Default
- Resource Groups — Logical groups of related resources that are deployed together. These can be assigned to Departments or Geographical Locations

Also, we can create monthly, quarterly or annual budgets. For the purposes of this demo (and the entire 100 Days), I’ll be using Subscriptions with a monthly budget.
Click on the “Budgets” menu option, and then click “Add”:

![image](https://user-images.githubusercontent.com/80047500/133889600-8e6a6348-f607-4825-8d2a-cc089ac7ed78.png)

This brings us into the “Create Budget” menu. Fill in the required details and set a Budget Amount — I’m going to set €50 as my monthly budget:

![image](https://user-images.githubusercontent.com/80047500/133889604-76a6a770-3803-4762-8d24-08a119c9636e.png)

Next, we need to set up Alert Conditions and email recipients. In Alert Conditions, we can see from the “Type” field that we can choose either Actual or Forecasted:

![image](https://user-images.githubusercontent.com/80047500/133889644-5c1af17c-4a3c-4bce-9b47-dc265c55368a.png)

Actual Alerts are generated when the monthly spend reaches the alert condition.
Forecasted Alerts are generated in advance when Azure calculates that you are likely to exceed the alert condition based on the services you are using.

Once you have your Alert Conditions configured, add one or more Alert Recipients who will receive alerts based on your conditions. Then click “Create”:

![image](https://user-images.githubusercontent.com/80047500/133889646-880e5079-69be-4673-9453-8f4c7d6fdd63.png)

And now we see our budget was created successfully!

![image](https://user-images.githubusercontent.com/80047500/133889785-f396994f-fa64-4e8f-9317-01f4ca67c9a1.png)

So, that’s the Azure Portal way to do it. There are 2 other ways, the first is using Azure PowerShell.

## Instructions - the Azure PowerShell Method

Firstly, we need open Windows PowerShell, and install the Azure Module. To do this, run:
“install -module -name Az”

![image](https://user-images.githubusercontent.com/80047500/133889651-61506db9-2b0b-4b23-b5d6-aab96c573cea.png)

This will install all packages and modules we require to manage Azure from PowerShell.

We can then run the following commands to create our Budget:

“Connect-AzAccount” will prompt us to log on to our subscription:

![image](https://user-images.githubusercontent.com/80047500/133889655-9344b258-2fcd-40bb-8abf-bb9760b1d409.png)

Once we are logged in, this will return details of our Subscription:

![image](https://user-images.githubusercontent.com/80047500/133889658-2eda1565-0e6a-4a82-955d-8dadede8f5b8.png)

Run “Get-AzContext” to check what level we are at in the subscription:

![image](https://user-images.githubusercontent.com/80047500/133890214-c0fff5d9-1a33-491a-ab61-8934d3e4d250.png)

Now, we can run the following command to create a new budget:

"New-AzConsumptionBudget -Amount 100 -Name TestPSBudget -Category Cost -StartDate 2021–09–17 -TimeGrain Monthly -EndDate 2023–09–17 -ContactEmail durkanm@gmail.com -NotificationKey Key1 -NotificationThreshold 0.8 -NotificationEnabled"

![image](https://user-images.githubusercontent.com/80047500/133890217-1c82f38f-ad83-4ec8-ab1b-5cb85676be33.png)

But it throws an error! Why?

It turns out that after a bit of digging, you can only set a budget using PowerShell if your subscription is part of an Enterprise Agreement. So I’m afraid because I’m using a free account here, its not going to work ☹.

Full documentation can be found at this link:

https://docs.microsoft.com/en-us/azure/cost-management-billing/costs/tutorial-acm-create-budgets#create-and-edit-budgets-with-powershell.

OK so lets move on to option 3, which is using Azure Resource Manager (ARM) Templates.

## Instructions - the Azure Resource Manager (ARM) Template Method

Simple method for this one, go to the following site:

https://docs.microsoft.com/en-us/azure/cost-management-billing/costs/quick-create-budget-template?tabs=CLI

And click on the “Deploy to Azure” button:

![image](https://user-images.githubusercontent.com/80047500/133890223-271a807e-9eac-48df-8e92-393db7fd4926.png)

This will re-direct us into the Azure Portal and allow us to fill in the fields required to create our Budget:

![image](https://user-images.githubusercontent.com/80047500/133890232-454abbd9-a34f-4188-aaca-205dd86f9550.png)

And that is how we create a Budget (3 ways) in Azure. See you on Day 3!!

## Social Media Proof

[Medium](https://durkanm.medium.com/100-days-of-cloud-day-2-azure-budgets-and-cost-management-f504a55d7f06)

[LinkedIn](https://www.linkedin.com/posts/michael-durkan-1a72a759_100-days-of-cloudday-2azure-budgets-and-activity-6844766743542411264-f_pL)

[Twitter](https://twitter.com/durkanm/status/1439001872371789828)
