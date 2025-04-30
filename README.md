# FUTURE_CS_01
 Web Application Security Testing Report
Target: http://testphp.vulnweb.com/artists.php
Tool Used: SQLMap
Test Type: SQL Injection Vulnerability Assessment


1. Executive Summary
This report outlines the results of a security test performed on the web application hosted at http://testphp.vulnweb.com/artists.php using SQLMap, an automated tool for detecting and exploiting SQL injection flaws. The objective was to identify potential SQL injection vulnerabilities that could compromise data confidentiality and integrity.

2. Objective
To identify whether the web application is vulnerable to SQL injection attacks and to evaluate the severity and potential impact of the discovered vulnerabilities.

3. Methodology
Tool Used: SQLMap

Test Type: Black-box penetration testing

Request Parameter Tested: artist or ID-based parameter in URL

Payload Injection: Automated SQLMap payloads

Commands Used:

bash
Copy
Edit
sqlmap -u "http://testphp.vulnweb.com/artists.php?artist=1" --batch --risk=3 --level=5 --dump
4. Findings
✅ Vulnerability Identified: SQL Injection
Vulnerable Parameter: artist

Injection Type: Error-based and Union-based SQL Injection

Database Identified: MySQL

Database Name Extracted: acuart

Tables Extracted: artists, carts, pictures, users

Sample Data Dumped (from users table):


ID	Username	Password (Hash)
1	test	5f4dcc3b5aa765d61d8327deb882cf99 (md5: "password")
5. Impact Analysis
If exploited by a malicious actor, the SQL injection vulnerability could lead to:

Unauthorized access to sensitive data (usernames, passwords, etc.)

Exposure of the backend database structure

Potential modification or deletion of database entries

Full compromise of application data integrity

6. Risk Rating
CVSS v3.1 Base Score: 8.8 (High)

Attack Vector: Network

Attack Complexity: Low

Privileges Required: None

User Interaction: None

Confidentiality Impact: High

Integrity Impact: High

Availability Impact: Low

7. Recommendations

Issue	Recommended Mitigation
SQL Injection	✅ Use parameterized queries or prepared statements
✅ Implement input validation and sanitization
✅ Employ Web Application Firewalls (WAF)
✅ Restrict database user privileges
✅ Regularly test for SQLi with automated tools
8. Tools Used
SQLMap – Automated tool for SQL injection detection and exploitation

Burp Suite (Optional) – For manual verification of HTTP requests/responses

OWASP ZAP (Optional) – For additional vulnerability scanning

9. Conclusion
The application is confirmed to be vulnerable to SQL injection attacks. Immediate remediation steps should be implemented to prevent exploitation. Continuous monitoring, periodic penetration testing, and secure development practices are recommended to mitigate future risks.

