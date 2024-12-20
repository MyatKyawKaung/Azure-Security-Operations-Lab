## What are STIX and TAXII?

**STIX (Structured Threat Information Expression)** and **TAXII (Trusted Automated Exchange of Indicator Information)** are standards for sharing threat intelligence data.

- **STIX** defines a language to structure cyber threat intelligence, enabling organizations to describe and share information in a common format.
- **TAXII** is a protocol used to exchange STIX data securely and efficiently.

These standards enable organizations to share threat intelligence data, aiding in the detection and prevention of cybersecurity threats.

**In this demo, we will integrate threat intelligence feeds into Microsoft Sentinel to enhance detection capabilities, respond proactively to threats, and leverage external threat data to improve our security operations.**

## Configure the Threat Intelligence TAXII Connector in Microsoft Sentinel

### 1. Install the Threat Intelligence Connector

Navigate to the **Microsoft Sentinel Content Hub** and install the **Threat Intelligence Connector**.

![1](https://github.com/user-attachments/assets/47dd785f-8e58-49f9-8851-b7e32785db36)


### 2. Open the Data Connector Page

Locate and select the **Threat Intelligence TAXII Connector** from the data connectors blade.

![2](https://github.com/user-attachments/assets/e08c5ff1-454b-4f0e-8adf-de9dd4c6f722)


### 3. Set Up a TAXII Feed Provider

To test the integration, use a free TAXII service like PulseDive. You can sign up here https://pulsedive.com/register

![3](https://github.com/user-attachments/assets/20e6a760-d2c8-42c4-95b0-77502780e070)


Create an account on the **PulseDive** platform.

![4](https://github.com/user-attachments/assets/93b9a33b-3c84-4a48-a3cb-04aa5ef6ac21)
![5](https://github.com/user-attachments/assets/737a2940-7a41-477b-8f69-bef74ec54172)


Retrieve the **API Root URL** and **API Key** from the account settings as shown in figures.

![6](https://github.com/user-attachments/assets/9c4d94a7-e568-49ca-b88c-bb892d2d4cb3)

![7](https://github.com/user-attachments/assets/454650f9-c7b6-44d0-88c2-25a0f865baf7)


### 4. Configure the Connector in Microsoft Sentinel

Enter the details (API Root URL, Collection, and API Key) into the Threat Intelligence TAXII Connector configuration page in Sentinel.

![8](https://github.com/user-attachments/assets/16d74d82-47d5-43e4-b355-e44e84f0a860)


After setup, verify the Threat Intelligence TAXII Connector shows as **connected**.

![9](https://github.com/user-attachments/assets/ae6450a3-898c-43dd-9a92-1fce15fc9bdf)


You can now view and access **Threat Intelligence Indicators** under the Threat Intelligence blade in Sentinel to view and analyze data feeds.

![10](https://github.com/user-attachments/assets/7a7ceddb-ef38-4571-884d-2a79001b76f2)


### 5. Utilizing Threat Intelligence for Analytics and Detection

To create an analytic rule with TI Feeds, we will develop a detection rule using **Threat Intelligence Indicators** and **Windows Security Event logs.**

![11](https://github.com/user-attachments/assets/48c0cfba-71ab-4bd0-bba7-97fb921efdf2)


Use the following KQL to join the **ThreatIntelligenceIndicator** table with the **SecurityEvent** table to identify suspicious activities, such as RDP brute-force attempts.

```kql
SecurityEvent
| join kind=inner ThreatIntelligenceIndicator
on $left.IpAddress == $right.NetworkSourceIP
| project EventID, TargetUserName, DomainName, NetworkIP, Url
```

![12](https://github.com/user-attachments/assets/12f077c3-2291-4ddf-aebc-cc4874056514)

Create a scheduled query rule with TI data.

![13](https://github.com/user-attachments/assets/332998e9-bf01-4081-97fe-3934546bb4ad)
![14](https://github.com/user-attachments/assets/4c8b65dc-32a5-4237-8e81-29a1e43f88c6)

Define the rule's logic using the KQL query we previously created for this alert.

![15](https://github.com/user-attachments/assets/2a8f777a-c8c2-4fd1-84d6-418bbb81423b)

Set a schedule for analytic rule to run (e.g., every 12 hours for the last 12 hours).

![16](https://github.com/user-attachments/assets/cbc6ff7d-3f5e-406b-b0a5-eb041d54139a)

Once everything is validated, save the rule to enable detection as shown below.

![17](https://github.com/user-attachments/assets/49e57aa6-cb92-4fb6-9b6b-e4d105f68f68)
