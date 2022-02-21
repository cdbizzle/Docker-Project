# Docker-Project
For this project I followed a guide from Medhat Elmasry building a PHP and MySQL Web App. I added my own twist by cloning an HTML page and adding it to the web page.
1. To start, you need a machine running with Docker installed, navigate to (https://docs.docker.com/get-docker/) to get started.
2. From your home directory, create and change to a new directory for this project, I named mine _php-mysql-app_: ```mkdir php-mysql-app``` followed by ```cd php-mysql-app```. Your command line should now look like this:<br/>![image](https://user-images.githubusercontent.com/71033480/155025361-f91cb2a8-f1c6-4fd1-85ae-26094774ef1e.png)
3. From within _php-mysql-app_ create a directory called _src_, this will be used to store the source code: ```mkdir src```.
4. Inside of _src_ create a text file called _index.php_: ```vi index.php```. Using _vi_ will create and open the file to edit. Paste the following the code inside:
```
<!DOCTYPE html>
<html lang="en">
<head>
<title>Show databases in MySQL server</title>
<meta http-equiv="content-type" content="text/html; charset=iso-8859-1" />
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">
</head>
<body>
<div class="container">
<h1>Show databases in MySQL server</h1>
<?php

getenv('MYSQL_DBHOST') ? $db_host=getenv('MYSQL_DBHOST') : $db_host="localhost";
getenv('MYSQL_DBPORT') ? $db_port=getenv('MYSQL_DBPORT') : $db_port="3306";
getenv('MYSQL_DBUSER') ? $db_user=getenv('MYSQL_DBUSER') : $db_user="root";
getenv('MYSQL_DBPASS') ? $db_pass=getenv('MYSQL_DBPASS') : $db_pass="";
getenv('MYSQL_DBNAME') ? $db_name=getenv('MYSQL_DBNAME') : $db_name="";

if (strlen( $db_name ) === 0)
  $conn = new mysqli("$db_host:$db_port", $db_user, $db_pass);
else 
  $conn = new mysqli("$db_host:$db_port", $db_user, $db_pass, $db_name);

// Check connection
if ($conn->connect_error) 
	die("Connection failed: " . $conn->connect_error);
 
if (!($result=mysqli_query($conn,'SHOW DATABASES')))
    printf("Error: %s\n", mysqli_error($conn));

echo "<h3>Databases</h3>";

while($row = mysqli_fetch_row( $result ))
    echo $row[0]."<br />";

$result -> free_result();
$conn->close();
?>
</div>
</body>
</html>
```

