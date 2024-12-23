Incident management is the process of identifying, analyzing, containing, eradicating, and recovering from security incidents within an organization's IT infrastructure.

This lab provides a structured approach to utilizing Microsoft Sentinel’s incident management capabilities effectively.

## **1. Reviewing Microsoft Sentinel Incident Blade**

To begin working on security incidents (tickets/jobs/cases) within Microsoft Sentinel, SOC analysts should start on the **Incidents** page. This page, found within the Sentinel workspace, initially displays all open incidents from the previous 24 hours. 

The filter bar offers options to modify the displayed incidents by:

- Changing the time window.
- Filtering by severity levels.
- Viewing incidents with different statuses (New, Active, or Closed)

![1](https://github.com/user-attachments/assets/3a2a748b-5965-463a-bfd3-97a6fe478671)

Beyond the **Incidents** page, the **Security efficiency workbook** on the top right offers an alternative perspective for incident review and provides a high-level assessment of SOC health. 

![2](https://github.com/user-attachments/assets/5e672501-f797-40ea-9551-6b7d573029ed)

The **Security Efficiency Workbook** provides visualizations and insights, such as:

- Incident severity levels.
- Mean Time to Triage (MTTT).
- Mean Time to Closure (MTTC).
- Incident status at a glance.

![3](https://github.com/user-attachments/assets/e73f4d21-c281-48cb-b2d8-b8b4015b20e4)
![4](https://github.com/user-attachments/assets/a5ba876d-1464-43d4-89f4-571331fbe550)
![5](https://github.com/user-attachments/assets/bb907941-dd37-4b62-9911-1e6fee127ce2)
![6](https://github.com/user-attachments/assets/d63cd017-d7d9-4b67-9036-5306e8a4250a)

## **2. Handling the incidents**

Navigate to the **Incidents** view of your Sentinel workspace. From the list of active incidents, select the incident that you want to investigate.

![7](https://github.com/user-attachments/assets/ca9081ff-3f51-46a8-bc05-2ea4ac685ec1)

**Take ownership of the incident** and **change its status to Active.** Click **View full details** to open the incident details pane.

![8](https://github.com/user-attachments/assets/ae29dba1-d633-402c-aec4-92c8d060248d)

Review the **Incident Timeline** to view alerts. Click on individual alerts and select **Link to LA** to access raw logs.

![9](https://github.com/user-attachments/assets/ef6606bc-c20d-4fb9-bb48-f8f41c684061)

In the logs, you can extract detailed information of interest, such as the activity's timestamp, the source IP address, associated user accounts, or other data points that help piece together the puzzle.

![10](https://github.com/user-attachments/assets/b406c1b1-db0b-42b5-be69-3714f35c4a6d)

To gather additional context, such as geographic details for an IP address, run a preconfigured playbook. This step is part of incident enrichment and may be automated in a real SOC environment.

![11](https://github.com/user-attachments/assets/0ca2fca3-2634-4612-b11e-0181c2fcd3a0)

After running the playbook, visualize enriched data by using investigation insights workbook.

![12](https://github.com/user-attachments/assets/4e609b78-ea5f-46e0-8a0b-71668ae44eee)
![13](https://github.com/user-attachments/assets/f0511ba9-7eb5-4751-b210-a9a8179f78c5)

You can see the number of alerts were created during the specific time range.

![14](https://github.com/user-attachments/assets/edf19fc2-9d4b-4e75-bc54-f19a003290ee)

Add the suspicious IP address or other entities of interest.

![15](https://github.com/user-attachments/assets/47bac409-8089-4393-9692-f775fcc841b7)

You can see all the activity done by this user account that associated with suspicious IP.

![16](https://github.com/user-attachments/assets/bd32f16f-1791-4ac5-baf4-4d25b162f99d)

## **3. Handover the incident**

Once you’ve completed the investigation and taken necessary actions, prepare the incident for handover. This typically involves documenting the findings and actions taken.

Open the investigated incident in the **Incidents** page and click **View full details.**

![17](https://github.com/user-attachments/assets/63a528b3-fd4b-4649-9878-b86b36bc72b6)

Navigate to the **Comments** tab and add documentation. That might include summary of findings, actions performed and recommendations for the team.

![18](https://github.com/user-attachments/assets/22573804-d3bd-44fd-b1ee-7d6b92e1913a)

Microsoft Sentinel provides a comprehensive set of tools for effective incident management. By leveraging its features, SOC teams can efficiently manage, investigate, and resolve security incidents.
