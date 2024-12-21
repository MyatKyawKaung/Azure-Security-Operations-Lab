The **Microsoft Sentinel Training Lab Solution** provides a hands-on environment by ingesting pre-recorded data, artifacts, custom tables that enable you to practice incident detection, investigation, and response within Sentinel.

## 1. Install Microsoft Sentinel Training Lab Solution

In the **Azure Portal**, search for **Microsoft Sentinel Training Lab Solution**.

![1](https://github.com/user-attachments/assets/1f5e4801-5bac-4b60-9031-b9b0309bf508)

Select the solution and click **Create** to initiate the setup.

![2](https://github.com/user-attachments/assets/07c492d4-b712-4339-8e0e-a8c4136274fc)

Choose the appropriate **Resource Group** and **Log Analytics Workspace** to store the custom data.

![3](https://github.com/user-attachments/assets/c1abb7d1-e26b-46fb-bb1c-61b417da9a62)

You can leave Workbooks, Analytics and Playbooks display name as default. Review the configuration and click **Create**.

![4](https://github.com/user-attachments/assets/3f975e9c-739c-4236-9264-0712a0ce25b8)
![5](https://github.com/user-attachments/assets/7c1eaa55-72cc-4991-b7d5-592ade55ee1d)
![6](https://github.com/user-attachments/assets/6605f617-2430-4dce-bca3-baf46d1ea456)


The deployment process takes approximately **10 to 15 minutes**.

![7](https://github.com/user-attachments/assets/fdb57ff2-4a22-4e60-b43f-892189cd8827)
![8](https://github.com/user-attachments/assets/39fb94f9-ea05-4f4c-86c7-d532487ba324)


## 2. Authorize API Connection for Sentinel

The **API connection** must be enabled because the **Microsoft Sentinel Training Lab Solution** uses workflows and playbooks that depend on external integrations for automated actions, including:

1. **Geo-Tagging and Incident Enrichment**:
    - The API connection **`az.sentinel-Get-GeoFromIpAndTagIncident`** retrieves geolocation data for IP addresses in incidents.
    - This enrichment provides important context to security events by mapping IP addresses to their geographical locations.
2. **Ensuring Functionality of Playbooks**:
    - Sentinel playbooks need API connections to communicate with external systems and perform incident management tasks like tagging, categorizing, and updating.
    - These playbooks cannot run if the API connection is not enabled.

Navigate to the **Resource Group** used during setup and find the resource named **az.sentinel-Get-GeoFromIpAndTagIncident**.

![9](https://github.com/user-attachments/assets/b74c7e97-91f5-4ce3-8912-883526fc7626)

Go to the **General** blade and select **Edit API Connection**.

![10](https://github.com/user-attachments/assets/3bc40668-3612-42bc-9a92-22bbb06b679a)

Click **Authorize** and sign in using the Azure tenant account associated with your subscription.

![11](https://github.com/user-attachments/assets/cadd0ab9-dfbd-4e88-8c5b-8b561e5c8c2d)

After successful authorization, save the connection settings.

![12](https://github.com/user-attachments/assets/7df9a932-6be2-43aa-b318-f45e9de5bd1c)

### **Summary**

The Microsoft Sentinel Training Lab Solution is a practical tool to enhance your expertise in Sentinel by providing pre-ingested data and custom environments for exploration. Once deployed and authorized, it becomes a powerful platform for training and experimentation.
