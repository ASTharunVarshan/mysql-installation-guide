# MySQL ZIP Version Installation Guide (Windows)

This guide explains how to install MySQL Server using the **ZIP version** (no installer).  
You will manually configure the MySQL server, initialize it, and start using it via Command Prompt.


## Prerequisites

- Download the MySQL ZIP archive from:  
   [https://dev.mysql.com/downloads/mysql/](https://dev.mysql.com/downloads/mysql/)

- Extract the ".zip" file to:  
      C:/  (later change this from "C:/mysql-version-8.0.43" to "C:/mysql")

- Add "C:/mysql/bin" to your **Environment Variables → PATH**  
  *(Very Important Step)*

## Step 1: Create "data" Folder

Create a new folder:  
    C:/mysql/data

## Step 2: Create "my.ini" File

Inside "C:/mysql", create a file named "my.ini" and paste the following configuration:

[mysqld]
basedir=C:/mysql
datadir=C:/mysql/data
port=3306

## Step 3: Open Command Prompt as Administrator

Search for cmd, right-click and choose
Run as Administrator

## Step 4: Initialize MySQL Server

Run the following command:
mysqld --initialize --console

***Note: This will generate a temporary root password.
Copy the password shown in this format:
A temporary password is generated for root@localhost: i2AeEZ!6ufjd


## Step 5: Install MySQL as a Windows Service
mysqld --install MySQL

## Step 6: Start the MySQL Service
net start MySQL

## Step 7: Log in to MySQL Using Temporary Password
mysql -u root -p

You will see:
Enter password: Paste the temporary password you copied earlier.

## Step 8: Set Your Own MySQL Root Password
Run the following SQL commands:
ALTER USER 'root'@'localhost' IDENTIFIED BY '1234';
FLUSH PRIVILEGES;
Replace 1234 with your own secure password.

## Step 9: Test MySQL Login
Close the Command Prompt and open it again.
mysql -u root -p
Then type the password you just set (1234 in this example). You should be logged into MySQL.

***Now You Can Run Queries!
Example:
SHOW DATABASES;









