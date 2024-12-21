## Setting Up the Azure Activity Data Connector

The **Azure Activity** data connector imports audit logs of actions performed within your Azure subscription into Microsoft Sentinel. (Note: Ensure you have at least **Reader** permission for the Azure subscription.)

Navigate to the **Content Hub** in Microsoft Sentinel and locate **Azure Activity and Install.**

![1](https://github.com/user-attachments/assets/35054d76-bf5f-44db-a76d-2a6ac0fb1b7f)
![2](https://github.com/user-attachments/assets/df4a4ba2-81d3-4629-ba63-8e18db0968b3)

Click **Create** to start the setup process.

![3](https://github.com/user-attachments/assets/b8da80f6-e4be-425c-9f03-8279d3b9350b)

Choose the appropriate **resource group** and **Log Analytics Workspace** where data will be streamed. 
Review the settings and click **Create**.

![4](https://github.com/user-attachments/assets/80a6d4b7-2360-424b-9cbf-4742461f6caa)

Open the **Azure Activity Connector** from the **Data Connectors** blade.

![5](https://github.com/user-attachments/assets/205a3aac-9e10-4982-9360-0ac0f0c87df2)

Ensure you have at least **Reader** permission for the Azure subscription. 

![6](https://github.com/user-attachments/assets/c246d773-1feb-4ae2-8573-3397c230b074)

Launch the **Policy Assignment Wizard** to assign required policies

![7](https://github.com/user-attachments/assets/1f63754b-1841-481b-a279-b71dfc72d9de)

Define the scope by adding subscriptions and resource groups

![8](https://github.com/user-attachments/assets/8f82af4e-e8f4-4781-b28a-91210455099a)

On the **Parameters** tab, select the primary Log Analytics Workspace

![9](https://github.com/user-attachments/assets/af4eba6a-d44a-43d8-a0b4-a2d4232fd017)


Enable the remediation task to ensure proper configuration.

![10](https://github.com/user-attachments/assets/ca525c80-bacb-4bf4-bfdf-2fbdab055fc3)

You can review and create once configuration are validated.

![11](https://github.com/user-attachments/assets/7debc109-306e-4dee-9d81-c0e9d19cf0cf)


## Configuring Microsoft Defender for Cloud Data Connector

The **Microsoft Defender for Cloud** data connector integrates cloud security events and recommendations into Sentinel. Before we install Defender for Cloud Data Connector, ensure **Microsoft Defender for Cloud** is activated for your Azure subscription.

Search for **Microsoft Defender for Cloud** in the Azure portal and navigate to **Environment Settings** under the **Management Blade.**

![12](https://github.com/user-attachments/assets/01dafcab-1d2f-4c27-9d3f-d7fc575c636b)

Select your Log Analytics Workspace and activate Defender.

![13](https://github.com/user-attachments/assets/407d57f0-290d-4f69-a8a4-afb6a6dac312)

In the **Content Hub**, locate **Microsoft Defender for Cloud**

![14](https://github.com/user-attachments/assets/4efc5acc-5cfc-4c98-887b-2a6df4671b3b)

Go to view details and Click Create.

![15](https://github.com/user-attachments/assets/12158880-08d7-4ba7-ab97-bd7b79c8b5c3)
![16](https://github.com/user-attachments/assets/32cccc54-bada-4455-b006-e633287f212b)


Select the **resource group, Log Analytics Workspace** and create.

![17](https://github.com/user-attachments/assets/e984985d-9050-4fe8-bb9d-2ffa0f31e752)
![18](https://github.com/user-attachments/assets/2f8f7106-db10-47cb-94f3-54e6ca3b3c7a)



On Data Connectors blade, select Microsoft Defender for cloud and open connector page.

![19](https://github.com/user-attachments/assets/6b8cd73c-deda-41a8-87f7-271a3726bc32)


Check the subscription and connection status.

![20](https://github.com/user-attachments/assets/ea536c20-a59e-4677-b8f7-5d409ee07fd6)

Verify Defender for Cloud data connector status as connected.

![21](https://github.com/user-attachments/assets/04a13eec-8a18-4aa9-8663-abad9398ca37)

**By configuring these data connectors, Microsoft Sentinel is equipped to ingest crucial logs and security events from Azure resources, enhancing visibility and enabling advanced threat detection.**
