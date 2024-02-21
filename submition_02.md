# Vulnerability to Man-in-the-Middle (MITM) Attacks due to Lack of HTTPS Implementation

### Severity: High

## Issue Description

The web application currently operates over unencrypted HTTP protocol, leaving it vulnerable to Man-in-the-Middle (MITM) attacks. Without encryption, sensitive data transmitted between the client and the server, such as login credentials and personal information, are exposed in plain text. This exposes the application to various security risks, including data interception, data tampering, credential theft, session hijacking, and phishing attacks. To mitigate these risks and enhance security, it's crucial to implement HTTPS encryption, which ensures the confidentiality, integrity, and authenticity of the transmitted data, thereby safeguarding against MITM attacks.


## Risk Rating

-   Risk: High
    
-   Difficulty to Exploit: Medium
    
-   Authentication : No

## Affected Target

-    I found this vulnerability at -  [http://52.66.188.78:31337/](http://52.66.188.78:31337/)


## Proof Of Concept

This web page uses HTTP for client-server communication. Therefor website is vulnerable for MITM attack.

### step 01

Open Wireshark and capture the packets.

<a href="https://ibb.co/LnwDdZT"><img src="https://i.ibb.co/vZ5C4jN/Wireshark.png" alt="Wireshark" border="0"></a>

### step 02

Get into your website login page and enter the credentials.

<a href="https://ibb.co/Gks1fzd"><img src="https://i.ibb.co/rMbLKDQ/login.png" alt="login" border="0"></a>

### step 03

Analyze the captured packets and find the credentials.

<a href="https://ibb.co/2qxfSyd"><img src="https://i.ibb.co/sjnMC2q/credentials.png" alt="credentials" border="0"></a>

## Business Impact

1.  **Reputation Damage**: Exploitation of this vulnerability could lead to breaches of sensitive customer data, resulting in negative publicity, loss of trust, and damage to the organization's reputation. Customers may perceive the business as insecure and unreliable, leading to decreased customer loyalty and potential loss of business.
    
2.  **Legal and Regulatory Consequences**: Depending on the nature of the data being transmitted, the organization may be subject to legal and regulatory penalties for failing to protect sensitive information adequately. Violations of data protection laws such as GDPR (General Data Protection Regulation) or industry-specific regulations can result in hefty fines, legal fees, and other financial liabilities.
    
3.  **Financial Losses**: In the event of a data breach or unauthorized access due to this vulnerability, the organization may incur financial losses from remediation efforts, legal fees, regulatory fines, and potential lawsuits from affected parties. Additionally, the loss of customers and damage to the brand's reputation can impact revenue and profitability in the long term.
    
4.  **Disruption of Operations**: If attackers exploit this vulnerability to compromise the web application or its underlying infrastructure, it could lead to disruptions in business operations, downtime, and loss of productivity. Depending on the criticality of the application to business functions, these disruptions could have significant financial and operational implications.
    
5.  **Competitive Disadvantage**: In industries where trust and security are paramount, such as finance, healthcare, or e-commerce, the presence of this vulnerability can put the organization at a competitive disadvantage compared to competitors who prioritize security and offer encrypted communication to their customers.

## Recommendations and Remediation

1.  **Implement HTTPS Encryption:** Transition the web application from unencrypted HTTP protocol to HTTPS to encrypt the communication between the client and the server. This can be achieved by obtaining an SSL/TLS certificate from a trusted certificate authority (CA) and configuring the web server to enable HTTPS.
    
2.  **Enable HTTP Strict Transport Security (HSTS**): Implement HSTS headers to instruct web browsers to only communicate with the application over secure HTTPS connections. This helps prevent downgrade attacks and ensures that users' browsers automatically redirect HTTP requests to HTTPS.
    
3.  **Update Internal Links and Resources:** Ensure that all internal links, resources (such as images, stylesheets, and scripts), and API endpoints within the web application are configured to use HTTPS. Update any hardcoded URLs in the application code or configuration files accordingly.
    
4.  **Perform Comprehensive Testing:** Conduct thorough testing of the HTTPS implementation to identify and address any potential issues or compatibility issues with browsers, devices, or third-party services. Test for mixed content warnings, insecure dependencies, and compatibility with older browser versions.
  
    
6.  **Educate Users**: Provide guidance to users on the importance of HTTPS and how to recognize secure connections in their web browsers. Encourage users to look for the padlock icon and "https://" prefix in the URL bar to verify the security of their connections.
    
7.  **Monitor and Update SSL/TLS Certificates:** Regularly monitor the expiration dates of SSL/TLS certificates and renew them before they expire to ensure uninterrupted HTTPS encryption. Implement automated processes for certificate renewal and deployment to prevent service disruptions.
    
8.  **Stay Informed About Security Best Practices**: Stay up-to-date with the latest security best practices and recommendations for securing web applications. Subscribe to security mailing lists, follow reputable cybersecurity blogs, and participate in relevant forums or communities to stay informed about emerging threats and vulnerabilities.



## References

 - https://www.tenable.com/plugins/nessus/48204
 - https://www.youtube.com/watch?v=DElzWHWDG9Q
 - https://www.fool.com/the-ascent/small-business/endpoint-security/articles/mitm/


