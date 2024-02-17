# Web Application Potentially Vulnerable to Clickjacking

### Severity: Medium

## Issue Description
The web server doesn't include essential security headers, such as X-Frame-Options and Content-Security-Policy 'frame-ancestors', in its content responses. This leaves the site vulnerable to clickjacking and UI redress attacks, where attackers can trick users into interacting with different parts of the page than they perceive, potentially leading to fraudulent or malicious actions.

X-Frame-Options, proposed by Microsoft, is a defense against clickjacking attacks and is supported by major browser vendors.

Content-Security-Policy (CSP), proposed by the W3C Web Application Security Working Group, is gaining support among major browser vendors. The 'frame-ancestors' directive within CSP restricts which sources can embed the protected resource.

Although there are other mitigation strategies like frame-busting JavaScript, X-Frame-Options and CSP are currently the most reliable methods for detection. As a result, this issue may result in false positives if alternative strategies are employed or if the page lacks security-sensitive transactions.


## Risk Rating

-   Risk: Medium
    
-   Difficulty to Exploit: Low
    
-   Authentication : No

## Affected Target

-    I found this vulnerability at -  [http://52.66.188.78:31337/](http://52.66.188.78:31337/)


## Proof Of Concept

The Nessus vulnerability scanner gives information to this webpage is vulnerable to clickjacking attack.

<a href="https://ibb.co/7jf8THQ"><img src="https://i.ibb.co/FmrNf9X/Screenshot-2024-02-17-133514.png" alt="Screenshot-2024-02-17-133514" border=""></a>

The following steps demonstrate how to exploit clickjacking vulnerability.

### Step 01

Open burpSuite and go to the target tab.

<a href="https://ibb.co/G76Myd3"><img src="https://i.ibb.co/313F2TY/Screenshot-2024-02-17-141500.png" alt="Screenshot-2024-02-17-141500" border="0"></a>

Then open the web browser and browse vulnerable web application.

<a href="https://ibb.co/rHd9SBb"><img src="https://i.ibb.co/2dZJQz8/Screenshot-2024-02-17-141949.png" alt="Screenshot-2024-02-17-141949" border="0"></a>

After that need go to burp tab and have to select **Burp Clickbandit** option. 

<a href="https://ibb.co/XpnLxqd"><img src="https://i.ibb.co/bL4m5ky/Screenshot-2024-02-17-142346.png" alt="Screenshot-2024-02-17-142346" border="0"></a>

Then need to click **copy cickbandit to ckickbord** button to copy the source code of clickbandit.

<a href="https://ibb.co/nncyDTf"><img src="https://i.ibb.co/RB0KC1P/Screenshot-2024-02-17-142504.png" alt="Screenshot-2024-02-17-142504" border="0"></a>

After coping the code have to paste it on the vulnerable web page Developer console. 

<a href="https://ibb.co/DtXtvkd"><img src="https://i.ibb.co/HVvVbYZ/Screenshot-2024-02-17-143053.png" alt="Screenshot-2024-02-17-143053" border="0"></a>

Then need to click the start button to record the clicks.

<a href="https://ibb.co/DpssJ0X"><img src="https://i.ibb.co/6BVVMjh/Screenshot-2024-02-17-143304.png" alt="Screenshot-2024-02-17-143304" border="0"></a>

After that can save the record for the POC.

here is the html document for the POC.

[POC for Clickjacking    Vulnerability](https://github.com/AvishkaDP/Project_Midsommer/blob/main/clickjacked.html)

## Business Impact

1.  **Data Breach Risk**: Clickjacking and UI redress vulnerabilities can potentially lead to unauthorized access to sensitive user data, resulting in data breaches. This could result in legal repercussions, fines, and damage to the company's reputation.
    
2.  **Financial Loss**: Clickjacking attacks can trick users into performing fraudulent transactions, resulting in financial losses for both the users and the business.
    
3.  **Reputation Damage**: Security vulnerabilities can tarnish the reputation of the business, making it less attractive to potential customers and partners.
    
4.  **Regulatory Compliance Issues**: Failure to implement adequate security measures may result in non-compliance with industry regulations and data protection laws, leading to penalties and legal consequences.
    
5.  **Operational Disruption**: Remediation efforts to address security vulnerabilities can disrupt normal business operations, leading to downtime and loss of productivity.

## Recommendations and Remediation

1.  **Implement X-Frame-Options Header**: Set the X-Frame-Options header with the value "SAMEORIGIN" or "DENY" to prevent the webpage from being embedded in a frame on other sites. This helps mitigate clickjacking attacks.
    
2.  **Implement Content-Security-Policy (CSP)**: Configure a Content-Security-Policy header with the 'frame-ancestors' directive to specify which domains are allowed to embed the webpage. This restricts the sources that can embed the protected resource, reducing the risk of UI redress attacks.
    
3.  **Stay Informed**: Keep track of updates and recommendations from security organizations, browser vendors, and industry experts regarding best practices for mitigating clickjacking and UI redress attacks.
    
4.  **Regular Security Audits**: Conduct regular security audits to identify and address any vulnerabilities in the web application, including those related to clickjacking and UI redress.
    
5.  **Training and Awareness**: Educate developers, administrators, and other relevant staff members about the importance of implementing security headers and following best practices to protect against clickjacking and UI redress attacks.
    
6.  **Use Security Tools**: Utilize automated security scanning tools and web application firewalls (WAFs) to detect and block clickjacking attempts and other security threats in real-time.
    
7.  **Test in Different Browsers**: Test the website in different browsers to ensure compatibility and effectiveness of the implemented security headers across various platforms.
    
8.  **Monitor and Respond**: Implement monitoring systems to detect and respond to any potential clickjacking or UI redress attacks in real-time, allowing for prompt mitigation actions.



## References

 - https://www.tenable.com/plugins/nessus/85582
 - https://www.youtube.com/watch?v=I9H28AdNNzQ
 - http://www.nessus.org/u?399b1f56
 - https://www.owasp.org/index.php/Clickjacking_Defense_Cheat_Sheet
 - https://en.wikipedia.org/wiki/Clickjacking


