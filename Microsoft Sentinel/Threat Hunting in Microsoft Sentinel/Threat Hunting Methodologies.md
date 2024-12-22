## What is Threat Hunting?

Proactive threat hunting involves actively searching for undetected threats in your environment rather than waiting for alerts from detection systems. By identifying threats early, you can prevent attackers from causing significant harm. Here’s a breakdown of the key concepts and steps involved:

## **Why Engage in Proactive Hunting?**

- **Avoid Severe Compromises**: Waiting for automated detections can lead to greater damage. Proactive hunting identifies threats before they escalate.
- **Hypothesis-Driven Approach**: Instead of searching for known indicators like IP addresses, focus on attacker techniques guided by hypotheses.
- **Operational Threat Intelligence**: Use threat intelligence to hypothesize tactics and techniques attackers may employ, enabling early detection.

## **Steps in Proactive Threat Hunting**

### **1. Develop a Hypothesis**

A hypothesis is the foundation of any threat hunt. A good hypothesis should:

- **Be Achievable**: Ensure you have the necessary data and knowledge.
- **Have a Narrow Scope**: For example, "Investigate unusual logins from a specific region."
- **Be Time-Bound**: Define the timeframe for investigation, such as the past week.
- **Focus on Gaps**: Target areas with limited detection coverage or historical blind spots.
- **Relate to Your Threat Model**: Ensure relevance to your organization's risks and environment.

Example Hypotheses:

- Investigate accounts running `cmd.exe` in the last 24 hours that hadn’t used it in the prior week.
- Detect unauthorized usage of PowerShell in sensitive regions.

### **2. Use MITRE ATT&CK Framework**

The MITRE ATT&CK framework provides a structured, comprehensive knowledge base of attacker tactics and techniques. Microsoft Sentinel integrates this framework to:

- **Visualize Coverage**: Analyze your current detection capabilities against known attacker techniques.
- **Develop Threat Models**: Use the framework to shape hunting hypotheses and understand potential attacker behavior.

### **3. Document the Process**

Thorough documentation is essential for repeatability and improvement:

- **What, How, and Why**: Explain the reasoning and methodology behind the hunt.
- **Input and Output**: Detail the data sources and results.
- **Replication Steps**: Enable other analysts to reproduce the hunt.
- **Next Steps**: Suggest follow-up actions, such as creating new alerts or refining monitoring capabilities

### **4. Follow-Up Activities**

After the hunt, regardless of whether active threats were found:

- **Set Up New Monitoring**: Based on findings, establish new detection rules.
- **Improve Detection**: Enhance existing rules to cover gaps revealed during the hunt.
