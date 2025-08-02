# 🐬 MySQL ZIP Version Installation Guide (Windows)

This guide explains how to install MySQL Server using the **ZIP version** (no installer).  
You will manually configure the MySQL server, initialize it, and start using it via Command Prompt.

---

## 🔧 Prerequisites

- 📦 Download the MySQL ZIP archive from:  
  👉 [https://dev.mysql.com/downloads/mysql/](https://dev.mysql.com/downloads/mysql/)

- 📁 Extract the `.zip` file to:  
  `C:/` (rename the folder from `mysql-version-8.0.43` to `mysql`)

- 🔄 Add `C:/mysql/bin` to your  
  **Environment Variables → PATH**  
  ✅ *Very Important Step*

---

## 📁 Step 1: Create `data` Folder

Create a folder at:  
`C:/mysql/data`

---

## 📝 Step 2: Create `my.ini` File

Inside `C:/mysql`, create a file named `my.ini`  
Paste the following content:
```
[mysqld]
basedir=C:/mysql
datadir=C:/mysql/data
port=3306
```

---

## 🖥️ Step 3: Open Command Prompt as Administrator

Search for `cmd`, right-click, and select:  
**Run as Administrator**

---

## ⚙️ Step 4: Initialize MySQL Server

Run this command:

mysqld --initialize --console

🔐 **Important:**  
This will generate a temporary root password like:

A temporary password is generated for root@localhost: i2AeEZ!6ufjd

Copy and save this password.

---

## 📌 Step 5: Install MySQL as a Windows Service

mysqld --install MySQL

---

## ▶️ Step 6: Start the MySQL Service

net start MySQL

---

## 🔐 Step 7: Log in Using Temporary Password

mysql -u root -p

When prompted:

Enter password:

Paste the **temporary password** you copied in Step 4.

---

## 🔒 Step 8: Set Your Own Root Password

Run the following SQL commands:

```
ALTER USER 'root'@'localhost' IDENTIFIED BY '1234';
FLUSH PRIVILEGES;
🔁 Replace 1234 with your own strong password.

✅ Step 9: Test MySQL Login
Close Command Prompt and reopen it. Then type:

mysql -u root -p
Now enter the password you set (1234 in this example).
You should be logged in successfully.
```
