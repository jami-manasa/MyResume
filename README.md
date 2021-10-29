# azure_cm
<details><summary><b>Common Imports for all Python Scripts:</b></summary>
<br>location source >> api >> imports<br>
    - <b></b>
<br>Import Azure SDK's for ClientSecretCredential,ResourceManagementClient,ComputeManagementClient<br>
    - **from azure.identity import AzureCliCredential**
 - **from azure.mgmt.resource import ResourceManagementClient**
 - **from azure.mgmt.compute import ComputeManagementClient**
 - **from azure.identity import ClientSecretCredential**
 - **from azure.mgmt.monitor import MonitorManagementClient**
</details>
<details><summary><b>01. virtual_machines.py</b></summary>
<br>
**Description:**
This script is to fetch the details of Azure virtual_machines details from Azure Portal and does insert / update/ delete operations on zs.virtual_machines table.
**Script Execution / Functional Flow**
- [ ] Fetch the list of Azue Subscriptions from ad.azure_subscriptions table
- [ ] Loop through the list of Azue Subscriptions
- [ ] Fetch the list of Resource groups from  Azue Subscriptions
- [ ] Get the  resource group wise virtual_machines details of a Azue Subscriptions by creating compute_client using azure.mgmt.compute module of Azure API client for Python
- [ ] Process the virtual_machines response into a dataframe
- [ ] If the dataframe is empty Remove records of specific Subscription from zs.virtual_machines table by Subscription_Id
- [ ] If the dataframe is not empty Update / Insert records of specific records into zs.virtual_machines table by Subscription_Id
![alt text]()
</details>
<details><summary><b>02. sql_databases.py</b></summary>
<br>
**Description:**
This script is to fetch the details of Azure Flexible databases details from Azure Portal and does insert / update/ delete operations on zs.flexible_databases table.
**Script Execution / Functional Flow**
- [ ] Fetch the list of Azue Subscriptions from ad.azure_subscriptions table
- [ ] Loop through the list of Azue Subscriptions
- [ ] Fetch the list of Resource groups from  Azue Subscriptions
- [ ] Get the  resource group wise flexible Databases Details of a Azue Subscriptions by creating compute_client using azure.mgmt.compute module of Azure API client for Python
- [ ] Process the Flexible Databases response into a dataframe
- [ ] If the dataframe is empty Remove records of specific Project from gz.flexible_databases table by Subscription_Id
- [ ] If the dataframe is not empty Update / Insert records of specific Project into zs.flexible_databases table by Subscription_Id
![alt text]()
</details>
