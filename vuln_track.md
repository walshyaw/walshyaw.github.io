---
title: Vulnerability Tracker
layout: home
nav_order: 5
---

# Vulnerability Tracker

---

**Repository:** [https://github.com/walshyaw/vulntrack](https://github.com/walshyaw/vulntrack)

A simple web application for logging and tracking CVE vulnerabilities, built with PHP and MariaDB.

## Features

- Log vulnerabilities with CVE-ID, CWE-ID, CVSS score, severity, exploit type, and more
- Edit and delete existing entries
- Sort table by any column

## File Structure

```
project/
├── index.php # Main page — displays table and form
├── save.php # Handles insert and update
├── delete.php # Handles row deletion
├── config.php # Database credentials
├── css/
│ └── styles.css
└── fonts/
├── DinaRemasterII.woff2
└── DinaRemasterII-Bold.woff2
```

## Setup

### 1. Database

Run the following SQL to create the database and table:

```sql
CREATE DATABASE vuln_track;
USE vuln_track;

CREATE TABLE vulns (
    id            INT AUTO_INCREMENT PRIMARY KEY,
    author        VARCHAR(100),
    cve_id        VARCHAR(20),
    cwe_id        VARCHAR(20),
    cvss_score    DECIMAL(3,1),
    exploit_avail TINYINT(1) DEFAULT 0,
    exploit_type  ENUM('rce','sqli','xss','privesc','lfi','other'),
    severity      ENUM('low','medium','high','critical'),
    product       VARCHAR(100)
);
```

### 2. Config

Fill in your database credentials in `config.php`:

```php
$host = "127.0.0.1";
$usr  = "your_username";
$pass = "your_password";
$db   = "vuln_track";
```

### 3. Requirements

- PHP 8.0+
- MariaDB / MySQL
- A local server (e.g. XAMPP, WAMP, or Apache + PHP)

## Usage

1. Fill out the form at the bottom of the page and click **+ SAVE VULNERABILITY**
2. Click **EDIT** on any row to load it into the form for editing
3. Click **DELETE** to remove a row
4. Click any column name in the sort sidebar to re-order the table

## Credits

- Font: [DinaRemasterII](https://github.com/zshoals/Dina-Font-TTF-Remastered/tree/master) by zshoals

## Built By

[@walshyaw](https://github.com/walshyaw)

---

*This project was made for educational purposes only.*