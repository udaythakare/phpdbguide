# Step-by-Step Guide: Connecting PHP to a MySQL Database using XAMPP

This guide explains how to connect PHP scripts to a MySQL database using XAMPP, a local development environment that includes Apache, MySQL, PHP, and Perl.

## Prerequisites

Before you begin, ensure you have the following:

- XAMPP installed on your computer. You can download XAMPP from [https://www.apachefriends.org/index.html](https://www.apachefriends.org/index.html).

## Step 1: Start XAMPP

1. Open XAMPP Control Panel:
   - On Windows: Search for "XAMPP Control Panel" and open it.
   - On macOS: Open Finder, navigate to the Applications folder, and then open the "XAMPP" folder. Double-click on "XAMPP Control" application.

2. Start Apache and MySQL:
   - Click on the "Start" button next to "Apache" and "MySQL" modules. This action starts the Apache web server and MySQL database server.

## Step 2: Create a MySQL Database

1. Open a web browser and go to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/). This is the phpMyAdmin interface provided by XAMPP to manage MySQL databases.

2. Log in using the default username "root" and leave the password field empty.

3. Click on the "Databases" tab in phpMyAdmin.

4. Enter a name for your new database in the "Create database" field and click the "Create" button.

## Step 3: Connect PHP to MySQL Database

1. Create a new PHP file in the "htdocs" directory of your XAMPP installation. You can find this directory inside the XAMPP installation folder. For example, `C:\xampp\htdocs` on Windows or `/Applications/XAMPP/htdocs` on macOS.

2. Open the PHP file in a text editor and use one of the following connection methods:
   
   - **Using MySQLi Extension:**
     ```php
     <?php
     $servername = "localhost"; // MySQL server address
     $username = "root";        // MySQL username
     $password = "";            // MySQL password (leave blank for XAMPP)
     $database = "your_database_name"; // MySQL database name

     // Create connection
     $conn = new mysqli($servername, $username, $password, $database);

     // Check connection
     if ($conn->connect_error) {
         die("Connection failed: " . $conn->connect_error);
     }
     echo "Connected successfully";
     ?>
     ```

   - **Using PDO Extension:**
     ```php
     <?php
     $servername = "localhost"; // MySQL server address
     $username = "root";        // MySQL username
     $password = "";            // MySQL password (leave blank for XAMPP)
     $database = "your_database_name"; // MySQL database name

     try {
         $conn = new PDO("mysql:host=$servername;dbname=$database", $username, $password);
         // set the PDO error mode to exception
         $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
         echo "Connected successfully";
     } catch(PDOException $e) {
         echo "Connection failed: " . $e->getMessage();
     }
     ?>
     ```

   Replace `"your_database_name"` with the name of the database you created in Step 2.

3. Save the PHP file and access it through your web browser by navigating to `http://localhost/your_file_name.php`, replacing `"your_file_name.php"` with the name of your PHP file.

## Conclusion

You've successfully connected PHP to a MySQL database using XAMPP. You can now start building dynamic web applications that interact with the database.
