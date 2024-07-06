# webpage-for-robot-movement
creating a webpage to control the robot's movement and connect it to a database

# downloading XAMPP 

the first step to create a webpage is to download XAMPP then after we open it we should start the Apache and MySQL

![Screenshot 2024-07-06 175208](https://github.com/FaisalBaqutyan/webpage-for-robot-mpvement/assets/174335196/90f2ca85-66e1-4380-a37c-62ac33aa885b)

# creating database

Next, I will open a web browser and go to http://localhost/phpmyadmin. then click on create database 

![Screenshot 2024-07-06 145822](https://github.com/FaisalBaqutyan/webpage-for-robot-mpvement/assets/174335196/268a7485-544d-4fff-acc8-2d9ebb485f1c)

i created a database called robot control then created a table called movement 

![Screenshot 2024-07-06 150559](https://github.com/FaisalBaqutyan/webpage-for-robot-mpvement/assets/174335196/bfc23b02-31b1-4e83-ae34-6ea6115dbdcf)

# creating a folder for the robot control 

then i went to the htdocs folder inside the XAMPP installation directory (C:\xampp\htdocs) and i created a new folder called robot_control 

![Screenshot 2024-07-06 150855](https://github.com/FaisalBaqutyan/webpage-for-robot-mpvement/assets/174335196/77d79ade-07d3-4642-ac05-f14413198f7d)


# creating the webpage 

inside this folder i used virtual studio code to write an html code that present the buttons on the webpage 

![Screenshot 2024-07-06 162546](https://github.com/FaisalBaqutyan/webpage-for-robot-mpvement/assets/174335196/f5402926-4bc0-4069-b11e-1e7cd9ff782b)

this is the code that i wrote 

```
<!DOCTYPE html>
<html>
<head>
<title>Robot Control</title>
</head>
<body>
    <h1>Control the Robot</h1>
    <form action="control.php" method="POST">
        <button type="submit" name="direction" value="forward">Forward</button>
        <button type="submit" name="direction" value="backward">Backward</button>
        <button type="submit" name="direction" value="left">Left</button>
        <button type="submit" name="direction" value="right">Right</button>
    </form>
</body>
</html>
```

# sending the data from the webpage to the database

Next, i created a php file inside the same folder and i wrote a code to send the data to the database 

![Screenshot 2024-07-06 162606](https://github.com/FaisalBaqutyan/webpage-for-robot-mpvement/assets/174335196/f68de6ca-d53d-489a-8aa5-ea21cff2f69f)


this is the code that i wrote 

```
<?php
$servername = "localhost";
$username = "root";
$password = "";
$dbname = "robot_control";

// Create connection
$conn = new mysqli($servername, $username, $password, $dbname);

// Check connection
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

if ($_SERVER['REQUEST_METHOD'] == 'POST') {
    $direction = $_POST['direction'];
    
    $sql = "INSERT INTO movements (direction) VALUES ('$direction')";
    
    if ($conn->query($sql) === TRUE) {
        echo "New movement recorded successfully";
    } else {
        echo "Error: " . $sql . "<br>" . $conn->error;
    }
}

$conn->close();
?>
```

Finally i went to http://localhost/robot_control/index.html to see the webpage and here is the webpage that i created 

![Screenshot 2024-07-06 162647](https://github.com/FaisalBaqutyan/webpage-for-robot-mpvement/assets/174335196/6fdc7a2b-89f4-4b35-8594-ed9d2d2abeb6)


here is the database that recived the data from the webpage 

![Screenshot 2024-07-06 162627](https://github.com/FaisalBaqutyan/webpage-for-robot-movement/assets/174335196/95ce1430-df0f-45c4-b75c-c03d608dfbcc)
