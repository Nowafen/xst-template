## XST Detection Template for Nuclei

This repository contains a Nuclei template developed by **MNM** to detect the presence of the HTTP `TRACE` method, which can lead to **Cross-Site Tracing (XST)** vulnerabilities — a high-risk but often overlooked threat.

<img width="1010" height="352" alt="image" src="https://github.com/user-attachments/assets/17947b1b-6c06-437a-9eb0-e583a6b8a634" />

### What is XST?
Cross-Site Tracing is a vulnerability that arises when a web server improperly supports the `TRACE` HTTP method. When enabled, this method reflects back the full request in the response — including headers such as `Cookie`, `Authorization`, and custom tokens. Combined with other vulnerabilities like **XSS**, it becomes a powerful vector for **session hijacking**, **information disclosure**, or **bypassing security flags** like `HttpOnly`.

### Severity: Critical

If vulnerable, the application could:
- Leak sensitive headers and credentials.
- Allow attackers to bypass session security.
- Be chained with client-side vulnerabilities like XSS to extract sensitive data via malicious JavaScript.

### Installations and use

To use this template:
1. Ensure you have [Nuclei](https://github.com/projectdiscovery/nuclei) installed.
2. Run the scan with:
   ```
   git clone https://github.com/Nowafen/xst-template.git
   nuclei -u https://domain.tld -t xst-template/
   ```
3. Review the response for `TRACE` method reflection.

## References
- OWASP: https://owasp.org/www-community/attacks/Cross_Site_Tracing  
- PortSwigger: https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-authentication-bypass

> Disable the TRACE method on production servers unless explicitly required for debugging — and even then, restrict it to internal use only.


Author: MNM
