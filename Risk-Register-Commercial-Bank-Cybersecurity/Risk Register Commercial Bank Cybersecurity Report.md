# **Risk Register: Commercial Bank Cybersecurity Assessment**

## **1\. Executive Summary**

This document presents a comprehensive risk register, a critical component of a proactive cybersecurity strategy for a commercial bank. The objective of this risk assessment is to identify, analyze, and prioritize potential risks to the bank's assets, information systems, and data. By systematically evaluating the likelihood and severity of various threats, this register provides a clear framework for allocating resources and focusing mitigation efforts on the most critical vulnerabilities. This aligns with the NIST Cybersecurity Framework (CSF) by establishing a robust process for managing cybersecurity risk.

## **2\. Operational Environment Analysis**

Understanding the operational environment is fundamental to an accurate risk assessment. The commercial bank operates within a specific context that influences its risk profile:

* **Location:** Situated in a coastal area with low crime rates. While low crime reduces certain physical security risks, the coastal location introduces environmental hazards (e.g., hurricanes) that could impact supply chains and physical infrastructure.  
* **Personnel:** The bank employs a significant workforce, including 100 on-premise and 20 remote employees. This distributed workforce increases the attack surface, particularly through remote access points and potential human error or social engineering vectors.  
* **Customer Base:** A substantial customer base of 2,000 individual accounts and 200 commercial accounts signifies a large volume of sensitive financial and personal data, making the bank an attractive target for cybercriminals.  
* **Marketing and Partnerships:** Marketing through a professional sports team and ten local businesses expands the bank's digital presence and potential third-party attack vectors.  
* **Regulatory Landscape:** Strict financial regulations necessitate stringent data and fund security measures. Non-compliance can result in severe fines, reputational damage, and loss of operating licenses, elevating the impact of security incidents.

## **3\. Risk Assessment Methodology**

The risk assessment methodology employed herein adheres to the widely accepted formula:

Likelihood×Severity=Risk Priority

* **Likelihood (1-3):** Estimates the probability of a risk event occurring.  
  * **1 (Low):** Rare, unlikely to occur.  
  * **2 (Moderate):** Likely to occur occasionally.  
  * **3 (High):** Certain, highly probable to occur frequently.  
* **Severity (1-3):** Estimates the potential impact or damage if a risk event occurs.  
  * **1 (Low Impact):** Minor disruption, minimal financial/reputational damage.  
  * **2 (Moderate Impact):** Noticeable disruption, some financial/reputational damage, minor regulatory issues.  
  * **3 (High Impact):** Catastrophic disruption, significant financial/reputational damage, major regulatory non-compliance, potential business closure.  
* **Priority (1-9):** The calculated risk score, indicating how urgently the risk should be addressed. Higher scores denote higher priority.

### **Sample Risk Matrix**

| Likelihood \\ Severity | Low (1) | Moderate (2) | Catastrophic (3) |
| :---- | :---- | :---- | :---- |
| **High (3)** | 3 | 6 | 9 |
| **Moderate (2)** | 2 | 4 | 6 |
| **Low (1)** | 1 | 2 | 3 |

## **4\. Risk Register**

The following table details identified risks to the bank's primary asset (Funds), along with their descriptions, estimated likelihood, severity, and calculated priority scores.

| Asset | Risk(s) | Description | Likelihood | Severity | Priority |
| :---- | :---- | :---- | :---- | :---- | :---- |
| Funds | Business email compromise | *An employee is tricked into sharing confidential information.* | 2 | 2 | 4 |
| Funds | Compromised user database | *Customer data is poorly encrypted.* | 3 | 3 | 9 |
| Funds | Financial records leak | *A database server of backed up data is publicly accessible.* | 2 | 3 | 6 |
| Funds | Theft | *The bank's safe is left unlocked.* | 1 | 3 | 3 |
| Funds | Supply chain disruption | *Delivery delays due to natural disasters.* | 1 | 2 | 2 |
| Notes | *How are security events possible considering the risks the asset faces in its operating environment?* |  |  |  |  |
|  | **Business email compromise:** Remote employees are susceptible to sophisticated phishing attacks, and a large employee base increases the chance of one employee falling victim. The bank's marketing efforts also make it a credible target for impersonation. |  |  |  |  |
|  | **Compromised user database:** The large customer base (2,000 individual, 200 commercial accounts) means a poorly encrypted database could expose vast amounts of sensitive financial data, leading to massive financial and reputational damage. |  |  |  |  |
|  | **Financial records leak:** The existence of a publicly accessible backup server for financial records presents a direct, high-impact vulnerability. While potentially an oversight, the exposure is critical given the regulatory environment. |  |  |  |  |
|  | **Theft:** Despite low crime rates, the bank's physical presence and the nature of its primary asset (funds) mean physical security vulnerabilities like an unlocked safe pose a direct, high-severity risk, even if the likelihood is low due to location. |  |  |  |  |
|  | **Supply chain disruption:** The bank's coastal location makes it susceptible to natural disasters (e.g., hurricanes) that can disrupt the delivery of essential supplies or services, impacting daily operations and regulatory compliance. |  |  |  |  |

## **5\. Prioritization and Mitigation Recommendations**

Based on the calculated priority scores, the cybersecurity team should focus its immediate attention on risks with higher scores.

* **Priority 9 (Highest):**  
  * **Compromised user database:** This risk, stemming from poorly encrypted customer data, poses the most significant threat. Immediate action is required to implement robust encryption protocols for all customer data, both in transit and at rest. Regular audits of database security configurations are critical.  
* **Priority 6:**  
  * **Financial records leak:** The publicly accessible backup server is a critical vulnerability. The immediate mitigation is to secure this server, restricting public access and implementing strong authentication and authorization controls. Data stored here should also be encrypted.  
* **Priority 4:**  
  * **Business email compromise:** Given the number of employees and remote work, this is a moderate priority. Mitigation strategies should include mandatory, regular cybersecurity awareness training for all employees (especially focusing on phishing and social engineering), multi-factor authentication (MFA) for all email accounts, and robust email filtering solutions.  
* **Priority 3:**  
  * **Theft:** While the likelihood is low, the severity is high. Physical security measures for the bank's safe and premises must be reviewed and reinforced. This includes strict access control, alarm systems, and clear protocols for securing high-value assets.  
* **Priority 2 (Lowest):**  
  * **Supply chain disruption:** This risk, while lower priority, still requires attention due to potential impacts on regulatory compliance. Developing a robust business continuity plan (BCP) and disaster recovery plan (DRP) that specifically addresses natural disaster scenarios and alternative supply chain routes is recommended. Establishing relationships with multiple vendors can also reduce reliance on a single point of failure.

## **6\. Conclusion**

This risk register provides a structured and prioritized view of cybersecurity risks facing the commercial bank. By systematically assessing likelihood and severity, the team can make informed decisions about resource allocation and mitigation strategies. This living document should be regularly reviewed and updated to reflect changes in the operational environment, threat landscape, and the effectiveness of implemented controls, ensuring the bank's continued resilience against evolving cyber threats.