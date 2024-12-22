### This lab will walkthrough how to perform a proactive threat-hunting procedure using Microsoft Sentinel’s hunting features.

Search for **Microsoft Sentinel** in the Azure portal and navigate to your Log Analytics workspace.

![1](https://github.com/user-attachments/assets/bdc3b0c5-4429-4c4a-ae52-220e97733965)

In Microsoft Sentinel, under the **Threat Management** blade, select **Hunting**. This displays all available hunting queries under the **Queries** tab.

![2](https://github.com/user-attachments/assets/ad59d02e-2fbe-47b4-8f4f-923348f39c3c)

The statistics display the number of active queries and required data sources in your environment. You can also see metrics for queries run in your current session, including livestream results and bookmarks created during hunting.

![3](https://github.com/user-attachments/assets/841d8637-8fa7-40ca-a6ad-2a1c0bbe331a)

The action bar at the top allows you to set the hunting timeline, create custom hunting queries, run selected queries, and delete queries.

![4](https://github.com/user-attachments/assets/f6a2a497-bdcd-4796-a406-6752ffc16cde)

### Exercise: Hypothesis to run hunting queries

“There might be potentially malicious PowerShell scripts being executed within our environment that are not being detected by our existing security solutions.

**Why Focus on PowerShell?**

PowerShell is often exploited for malicious purposes, including:

- Downloading malware.
- Establishing persistence.
- Data exfiltration.

This aligns with the **Living off the Land (LotL)** technique used by attackers.

### Queries to Test the Hypothesis

Use Microsoft Sentinel’s built-in hunting queries, such as:

1. **Exchange PowerShell Snapin Added**:
    
    Detects the loading of the Exchange PowerShell Snapin, often used by attackers on compromised servers.
    
2. **Invoke-PowerShellTcpOneLine Usage**:
    
    Identifies attempts to create reverse shells using this script.
    
3. **New PowerShell Scripts Encoded on the Command Line**:
    
    Detects encoded PowerShell commands, commonly used to obfuscate malicious activity.
    
4. **PowerShell Downloads**:
    
    Tracks PowerShell scripts downloading external files, a possible malware indicator.
    

### Execute Hunting Queries

Search for the keyword **PowerShell** in the search bar and select the desired queries and click **Run Selected Queries**.

![5](https://github.com/user-attachments/assets/e33051e8-5928-44fe-b283-bcf68ac70380)

Once the queries execute, their status updated to running state.

![6](https://github.com/user-attachments/assets/47eff468-5aec-4522-a32f-74b4a9a7be85)

Results are displayed under the **Results** column. (Note: In my lab environment, no malicious activity may be detected due to inactivity.)

![7](https://github.com/user-attachments/assets/dc810596-119a-4544-aedf-b907167d0ab7)

### MITRE ATT&CK Mapping

From our hypothesis, it relates to the **MITRE ATT&CK technique T1059: Command and Scripting Interpreter**

![8](https://github.com/user-attachments/assets/6326ee73-1cdd-4c6a-9b91-338c8b731483)

You can add filter hunting queries by **MITRE tactics and techniques.**

![9](https://github.com/user-attachments/assets/275507cb-4c13-4414-821e-fcec2f09512e)
![10](https://github.com/user-attachments/assets/e560d065-f68a-4d92-b49c-cec612e9b0f9)

It will show all the hunting queries associated with the TTPs.

![11](https://github.com/user-attachments/assets/a26c55fe-36e0-46de-afa7-411e214787bd)

### Additional Hunting Features

You can also add hunting query to livestream, create analytic rule, create a hunt or add to favourites.

![12](https://github.com/user-attachments/assets/8fe35624-4649-427c-a1cd-5a3e0712b212)

Once you added hunting queries into livestream, any new results on that Livestream instance will create a notification within the Azure user interface.

![13](https://github.com/user-attachments/assets/0b68d5fc-c2ce-4185-a44a-71da5f58a3d9)

You can add **bookmarks** on hunting query results. This can enable analysts to save, tag, annotate, share and investigate results from a Log Analytics query.

![14](https://github.com/user-attachments/assets/4c7c3686-7085-49f7-aaf7-b1d3387a4676)

You can also add the bookmarks to create or add to existing incidents as well.

![15](https://github.com/user-attachments/assets/67c7c9be-e6ab-41ab-91ca-83cdc81161e6)


