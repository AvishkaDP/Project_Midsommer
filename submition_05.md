# Web Server info.php / phpinfo.php Detection Detection

### Severity: High

## Issue Description


The PHP programming language is widely used for web development, and it includes a built-in function called `phpinfo()` that provides detailed information about the PHP installation and server configuration. While this function is intended for debugging and troubleshooting purposes, its unrestricted access can pose a significant security risk.

This vulnerability arises from the practice of creating PHP files that invoke the `phpinfo()` function, either for debugging purposes or as part of various PHP applications. When accessed by a remote attacker, these files inadvertently expose sensitive information about the server environment, allowing the attacker to gather valuable intelligence for potential exploitation.

Key information that can be obtained through the `phpinfo()` function includes:

1.  **Username and SUDO Privileges**: The username of the user who installed PHP, along with indications of whether they possess elevated privileges, such as SUDO access.
    
2.  **Host IP Address**: The IP address of the server hosting the PHP application, revealing its location on the network.
    
3.  **Operating System Version**: Details about the operating system running on the server, including version information, which could aid attackers in identifying vulnerabilities specific to that OS version.
    
4.  **Web Server Version**: Information about the web server software being used (e.g., Apache, Nginx), including version numbers, potentially exposing known vulnerabilities.
    
5.  **Root Directory**: The root directory of the web server, providing insights into the file structure and organization of the server's content.
    
6.  **PHP Configuration**: Comprehensive details about the PHP configuration, such as enabled modules, PHP version, and various settings, which can assist attackers in crafting more targeted exploits.
    

This vulnerability can be exploited remotely by simply accessing the PHP file containing the `phpinfo()` function call through a web browser or automated scanning tools. Once the attacker gathers this information, they can analyze it to identify potential weaknesses in the server configuration or target specific vulnerabilities to launch further attacks, such as privilege escalation, remote code execution, or unauthorized access to sensitive data.


## Risk Rating

-   Risk: High
    
-   Difficulty to Exploit: Medium
    
-   Authentication : No

## Affected Target

-     http://52.66.188.78:31337/


## Proof Of Concept


<a href="https://ibb.co/BNFc6V1"><img src="https://i.ibb.co/M6QZ1DX/POC3.png" alt="POC3" border="0"></a>

## Business Impact

1.  **Data Breach**: Exposing information such as the username of the user who installed PHP, whether they have sudo privileges, and the root directory of the web server can aid attackers in crafting more targeted attacks, potentially leading to unauthorized access or data breaches.
    
2.  **System Compromise**: By revealing the IP address, operating system version, and web server version, attackers can tailor their attacks to known vulnerabilities specific to the system, increasing the likelihood of successful compromise.
    
3.  **Reputation Damage**: If customer data or sensitive information is compromised due to this vulnerability, it can lead to a loss of trust from customers and stakeholders, damaging the organization's reputation.
    
4.  **Financial Loss**: Remediation efforts, legal fees, and potential fines resulting from a data breach can lead to financial losses for the organization.
    
5.  **Disruption of Service**: Depending on the severity of the attack, the organization may experience downtime or disruption of services, impacting productivity and revenue generation.
    
6.  **Regulatory Compliance Issues**: Depending on the industry, failing to adequately protect sensitive information may lead to violations of data protection regulations, resulting in legal consequences and financial penalties.

## Recommendations and Remediation

1.  **Remove or Secure phpinfo.php Files**: Identify and remove any phpinfo.php files from the web server directories. If phpinfo.php files are necessary for debugging purposes, ensure they are adequately secured by restricting access through authentication mechanisms or IP whitelisting.
    
2.  **Limit Information Exposure**: Modify the php.ini configuration file to restrict the information displayed by phpinfo(). Set the phpinfo() function to display only essential information required for debugging purposes, such as PHP version and loaded modules, while suppressing sensitive details like system paths and user information.
    
3.  **Regular Updates and Patch Management**: Keep PHP, the web server software, and the underlying operating system up to date with the latest security patches and updates. Vulnerabilities that expose sensitive information may be patched in newer releases, reducing the risk of exploitation.
    
4.  **Implement Access Controls**: Restrict access to sensitive directories and files on the web server using proper file permissions and access controls. Employ techniques such as directory indexing prevention and server hardening to minimize the exposure of critical information.
    
5.  **Security Awareness Training**: Educate system administrators and web developers about the risks associated with exposing sensitive information through phpinfo() and other debugging mechanisms. Encourage best practices for secure coding and configuration management to prevent inadvertent information disclosure.
    
6.  **Network Segmentation**: Implement network segmentation to isolate the web server from other critical systems and services. Limit the scope of potential attacks by compartmentalizing the network and controlling access to sensitive resources.
    
7.  **Monitor and Log Access**: Implement logging and monitoring mechanisms to track access to phpinfo.php files and other sensitive resources. Regularly review access logs for suspicious activity and investigate any unauthorized access attempts promptly.
    
8.  **Penetration Testing and Vulnerability Scanning**: Conduct regular penetration testing and vulnerability scanning to identify and address security weaknesses in the web server configuration. Utilize automated tools and manual testing techniques to assess the effectiveness of security controls and remediate any discovered vulnerabilities.



## References

 - https://www.tenable.com/plugins/nessus/11229
 - https://www.cyberciti.biz/faq/how-do-i-test-php-installation-with-a-phpinfo-page/


