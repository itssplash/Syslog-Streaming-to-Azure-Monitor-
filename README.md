# 🚀 Syslog Streaming to Azure Monitor  

## 📌 Overview  
This project involves configuring **syslog streaming** from an **Azure Linux Virtual Machine (VM)** to **Azure Monitor**, enabling real-time log monitoring and analysis.  

## 🛠️ Prerequisites  
- Azure account with permissions to create & manage resources  
- Basic knowledge of **Linux CLI** and **Azure Monitor**  

## 🏗️ Step 1: Create an Ubuntu VM  
1. In Azure Portal, create a new **Ubuntu VM**.  
2. Name the VM, including your **Algonquin username**.  

## 🛠️ Step 2: Install the Monitoring Agent  
1. In **Azure Portal**, search for **Monitor**.  
2. Navigate to **Monitor > Settings > Data Collection Rules**.  
3. Click on **+ Create** to add a new rule.  
4. Under **Basics**, enter:  
   - **Rule Name**  
   - **Subscription & Resource Group**  
   - **Region & Platform Type** (Select **Linux**)  
5. Click **Next: Resources** and select **+ Add resources**.  
6. Expand the **Subscription & Resource Group**, locate your **VM**, and click **Apply**.  
7. Click **Next: Collect and Deliver**, then **+ Add data source**.  
8. Choose **Linux Syslog** from the drop-down and add the data source.  
9. Click **Review + Create** and wait for validation.  
10. Click **Create** after validation is successful.  

## 🔧 Step 3: Configure Syslog Data Collection  
1. Open **Data Collection Rule > Data Sources**.  
2. Select **Linux Syslog**.  
3. Modify the **Minimum log level** for each **Facility**.  
4. Click **Save** after configuring log levels.  

## 📊 Step 4: Parse Logs in Azure Monitor  
1. Go to **Azure Monitor > Logs**.  
2. Select the scope of the **Virtual Machine**.  
3. Navigate to your VM and select it.  
4. Run the following **KQL query** to check syslogs:  
   ```kql  
   Syslog  
   | where Facility contains "auth"  
   ```  
5. Verify that the logs are being received in **Azure Monitor**.  

## ✅ Verification  
Ensure that your **Ubuntu VM syslogs** are successfully streaming to **Azure Monitor** and can be queried in **Log Analytics**.  

## 🧹 Cleanup  
If you no longer need the VM, delete it to avoid unnecessary costs:  
```sh  
az vm delete --name <your-vm-name> --resource-group <your-rg-name> --yes  
```  

## 🚀 Key Learnings  
- Setting up **syslog forwarding** from Linux to **Azure Monitor**  
- Using **Data Collection Rules (DCR)** for log ingestion  
- Querying **Azure Log Analytics** using **KQL**  
