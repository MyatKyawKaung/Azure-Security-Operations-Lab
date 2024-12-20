**This demo walkthroughs how to configure detection rules and dashboards in Microsoft Sentinel, enabling effective monitoring and investigation of security events such as RDP brute-force attempts.**

## **Step 1: Create Detection Rules in Sentinel**

Navigate to the **Analytics** blade in Microsoft Sentinel.

![1](https://github.com/user-attachments/assets/91457ac3-b9b8-45e6-a9bd-12a8b0529ab6)

Select **Create** to start a new scheduled query rule.

![2](https://github.com/user-attachments/assets/99509ba6-c4fa-4042-ba1c-be24fb410b8f)

Provide a clear name and description for the rule to ensure easy identification.

![3](https://github.com/user-attachments/assets/88226dde-e6c0-4ed7-ad42-ebbbacc7e815)

Set the rule logic. Use the following KQL query to monitor Event ID 4625 (failed login attempts):

```kql
SecurityEvent
| where EventID == 4625
| project TimeGenerated, WorkstationName, Computer, TargetUserName, LogonTypeName, IpAddress
| extend AccountEntity = TargetUserName
| extend IPEntity = IpAddress
```
![4](https://github.com/user-attachments/assets/744ccc1f-8908-49ca-be2d-baf8042f10d8)

**Configure Additional Details:**
- Set **Entity Mapping**, **Custom Details**, and **Alert Details** based on your organization's needs.
- Define the **schedule query runtime**

![5](https://github.com/user-attachments/assets/b360405e-3a1c-430b-ae69-485b41e8dd98)

Configure thresholds, grouping, and suppression logic to reduce false positives.

![6](https://github.com/user-attachments/assets/80e89969-3a1f-4db1-8ca0-e3b5e625346f)

Validate your configurations and click **Create.**

![7](https://github.com/user-attachments/assets/b59f2d52-269d-482b-a704-36cf14c5bfd0)

Verify and ensure the detection rule is enabled and actively monitoring for events.

![8](https://github.com/user-attachments/assets/bc198a2f-b498-48b5-9ad7-eea29db06665)

## **Step 2: Investigate Incidents**

To view detected incidents, Go to the **Incidents** blade to see alerts triggered by the analytics rule.

![9](https://github.com/user-attachments/assets/62d0b57e-52f4-45f8-a5ac-5659cbdb5152)

Review the incident overview, related entities, and assign it to an analyst. Change the status to **In Progress** as needed.

![10](https://github.com/user-attachments/assets/dad83ede-e188-4e5b-9860-bda7ee765493)

Use the **Investigation** tab for a visual representation of related entities as below.

![11](https://github.com/user-attachments/assets/1dcaa77f-e4bd-4e52-861f-529bc9366dcf)

If you want to dive deeper, click **Events** to query logs for further investigation. Run KQL query for further investigation, you can see the event logs as in shown in figure.

![12](https://github.com/user-attachments/assets/d3085538-c55a-4ff6-8699-868479b17680)

## **Step 3: Monitor RDP Brute Force Attempts**

**KQL Query for Workbook:**

```kql
SecurityEvent
| where EventID == 4625
| where isnotempty(IpAddress)
| extend GeoInfo = geo_info_from_ip_address(IpAddress)
| project TimeGenerated, TargetUserName, IpAddress, GeoInfo.country, GeoInfo.latitude, GeoInfo.longitude
```
![13](https://github.com/user-attachments/assets/fa37e2e1-27b4-431f-b738-aa4cd67e5cef)

Navigate to the **Workbooks** section and click **Add Workbook**.

![14](https://github.com/user-attachments/assets/aea471fb-5ab1-4fd3-8c0e-0948581018f5)

Add a query and set visualization to **Map** for a geographic representation.

![15](https://github.com/user-attachments/assets/ae6a3dc7-dede-4849-a950-95cb6d4c0131)
![16](https://github.com/user-attachments/assets/0301afd2-61b3-4323-8f24-a5e13a5bb874)

Set visualization to **Map** for a geographic representation.

![17](https://github.com/user-attachments/assets/37f81265-c3e1-41b1-bd2c-cd33beeaa4f3)

Specify the visual map settings according to your preferences.

![18](https://github.com/user-attachments/assets/80530eda-3e52-4f72-9331-89930f37ff5c)

Give the dashboard a title under **Advanced Settings**

![19](https://github.com/user-attachments/assets/2f82ead4-5ee2-48dd-a526-bf39551b4917)

Once everything is set, save the workbook as a dashboard with a descriptive name.

![20](https://github.com/user-attachments/assets/b5721d0c-aa58-44d7-9d8f-35dc1f717623)

Now you can monitor login attempts on your VM in real-time using the created dashboards.

![21](https://github.com/user-attachments/assets/94155e54-b29a-448d-ba84-cd82dd37cad9)

You can create a similar dashboard for monitoring successful logins as well.

![22](https://github.com/user-attachments/assets/da5c641f-1b94-487b-b438-4e11c213606d)

**By following this guide, you can effectively configure detection rules and dashboards in Microsoft Sentinel to monitor and respond to RDP brute-force attempts and other security events.**
