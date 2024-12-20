**This demo walkthroughs the step-by-step process of creating a virtual machine in Azure, connecting it to Log Analytics workspace, setting up Sentinel, and ingesting windows security event logs into Sentinel.**

## Step 1: Create a Resource Group

The first step is to create a resource group to organize your lab resources. Navigate to **Azure Portal** and search for **Resource Groups**. Click **Create**

![1](https://github.com/user-attachments/assets/15c861de-e3dc-4746-b131-e1f5fbc3eae9)

Provide a name (e.g., `Sentinel-Demo-Lab`), and choose a region.

![2](https://github.com/user-attachments/assets/26b56952-a8f5-4812-a879-84e1cba39e32)

Once created, the resource group will serve as a container for all subsequent resources.

![3](https://github.com/user-attachments/assets/df4fbf2e-e720-4602-bbbb-4c60c5b166f6)


## Step 2: Create a Virtual Machine (VM)

Search for **Virtual Machines** in the portal.

![4](https://github.com/user-attachments/assets/8257b9c7-b75e-40e6-9239-f051fbd909da)

Click **Create** and choose **Azure Virtual Machine**.

![5](https://github.com/user-attachments/assets/445db981-8728-404c-bd32-2c48359fcc60)

Configure the following:
- Select the previously created resource group.
- Specify the VM name and operating system (e.g., Windows Server).
- Choose an appropriate size (e.g., Standard B1s for testing).

![6](https://github.com/user-attachments/assets/c5cf80ad-d565-433d-8560-85e3252882cd)

Once everything is set, review and create your VM.

![7](https://github.com/user-attachments/assets/c9786e73-a575-480f-9685-cc6cf0ba1aa0)


Allow RDP (port 3389) for lab purposes by adding an inbound security rule in the network security group settings.

![8](https://github.com/user-attachments/assets/d3732e90-663c-4b67-a2d3-665d1c89ae68)
![9](https://github.com/user-attachments/assets/271fd094-39fe-4ebb-b4e1-74ea9c0fff4f)

## Step 3: Log Analytics Workspace Setup

The purpose of Log analytics workspaces is to ingest windows security logs from VM into it so we can search and investigate logs with Sentinel.

Search for **Log Analytics Workspaces** in Azure portal.

![10](https://github.com/user-attachments/assets/e94f9a22-672f-465b-bb91-0fa500ad480e)


Click **Create**, select the previously created resource group and provide a descriptive name. Once created, this workspace will be used to ingest security logs from the VM.

![11](https://github.com/user-attachments/assets/81fa0099-6527-499c-86ed-22d3bd1c9773)


## Step 4: Connect the VM to Log Analytic

Down RDP file or Connect RDP with Publick IP to VM.

![12](https://github.com/user-attachments/assets/f7dec28f-a867-4f40-ab5f-89afa5ca9c02)


In Log-Analytics Workspace, download the Azure Monitor Agent (AMA) from the workspace by copying the download link. Copy the Download Windows Agent (64bit) or (32bit) according to your VM.

![13](https://github.com/user-attachments/assets/5247e0ef-5b9f-4167-a087-75dbb9084e6d)

Connect to the VM via RDP, paste the link in a browser and install the agent using the setup wizard as below figures.

![14](https://github.com/user-attachments/assets/5af8a9ca-6141-464b-8045-1d21848467df)
![15](https://github.com/user-attachments/assets/042fae9a-9f38-46fd-8ae6-16a4a4bad8f3)
![16](https://github.com/user-attachments/assets/e2d26dff-85aa-41e7-8986-4071382d3f67)
![17](https://github.com/user-attachments/assets/3bd5fa70-8b7e-40e7-ac24-5e9e761db003)
![18](https://github.com/user-attachments/assets/b38614b7-1626-4667-a4f3-6e8959a36fe3)
![19](https://github.com/user-attachments/assets/c40c0466-1184-47fa-9791-d306f7f2c439)
![20](https://github.com/user-attachments/assets/33997379-1bbf-4379-829d-3469a1b49d36)

Verify the agent connection in the Log Analytics workspace under **Agents Connected**. You can see AMA agent form VM is connected to Log Analytics workspace.

![21](https://github.com/user-attachments/assets/b1a7ef1b-7bbb-4b70-91d0-40d74c174c7e)

You can see AMA agent is start forwarding logs to Log Analytics workspace.

![22](https://github.com/user-attachments/assets/b85b6a59-8e56-4939-a7ac-d19d37cef83c)


## Step 5: Configuring Microsoft Sentinel

Navigate to **Microsoft Sentinel** in the Azure portal and Click **Create.**

![23](https://github.com/user-attachments/assets/13e24bce-7c2e-4130-8550-a6f2a81e5ad9)


Select the Log Analytics Workspace created earlier and enable Sentinel for that workspace.

![24](https://github.com/user-attachments/assets/47941104-4810-40cd-b13d-4998e93673cf)

Once Microsoft Sentinel is enabled, you will get Sentinel free trial for 31days.

![25](https://github.com/user-attachments/assets/f3ab8768-bd97-43bc-b51d-2efd5fff3988)

## Step 6: Configure Data Collection Rule

Search for **Windows Security Events** in the **Content Hub** and install the connector.

![26](https://github.com/user-attachments/assets/0bda714a-c0fa-4a12-946e-176361a48db3)


Once **Windows Security Events** connector is installed from the content hub, go to **Data Connectors** blade and open the connector page.

![27](https://github.com/user-attachments/assets/2c41a84b-d149-4782-9887-37ed74f1f249)


Create a Data Collection Rule (DCR) to collect security events from the VM.

![28](https://github.com/user-attachments/assets/3d6e4601-22e9-4b43-a502-7e4460f2b8c6)


Provide a Data Collection Rule name and select the resource group.

![29](https://github.com/user-attachments/assets/168989cd-ee8b-495f-8780-d1bb5d9cd285)

Assign the DCR to your VM.

![30](https://github.com/user-attachments/assets/99bd02e9-cb2c-412c-aa83-6c26a6078267)


You can specify your DCR to collect All events, Common, Minimal or Custom according to your organization requirements.

![31](https://github.com/user-attachments/assets/7d5f262d-19c1-42c9-af83-dc1aa1e03bcf)

![32](https://github.com/user-attachments/assets/40cee575-02af-43e8-95eb-556f4d616270)

Create DCR once configurations are validated.

![33](https://github.com/user-attachments/assets/a0226033-9f2c-4ac9-8e27-aa795fcff567)


You can verify Windows Security Events Connector is connected or not under **Data Connectors** blade.

![34](https://github.com/user-attachments/assets/f2f42938-f4b2-4801-bfbb-d1d00344b82f)

