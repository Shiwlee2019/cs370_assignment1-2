#  CS370 File Upload Servlet Project – Spring 2025

This project demonstrates a servlet-based file upload system integrated with a **remote MySQL database** and deployed via **Apache Tomcat** behind an **Apache 2.4 reverse proxy** on an AWS EC2 instance.

---

## 
📎 [View Live System](http://3.143.247.27/upload/index.html)

---

##  WAR File Name
```
cs370_s25fileuploadServlet-rahman-shiwlee.war
```

---

##  Features Implemented

| Feature Level | Description                                                                 | Status |
|---------------|-----------------------------------------------------------------------------|--------|
| Level 1       | Deployable WAR with correct naming convention                               | ✅     |
| Level 2a      | File content stored remotely in a MySQL database                            | ✅     |
| Level 2b      | Upload size restriction: Reject files > 50MB using `@MultipartConfig`       | ✅     |
| Level 3       | Supports SQL-based inspection like `OCTET_LENGTH(file_content)`             | ✅     |
| Level 4       | End-to-end remote integration via Apache reverse proxy on EC2               | ✅     |

---

## Technologies Used

- **Java Servlets** (JDK 11+)
- **Apache Tomcat 9**
- **Apache 2.4** (Reverse Proxy)
- **MySQL 8.0** (Remote DB)
- **AWS EC2** (Ubuntu Linux)
- **Maven** (Project Structure)
- **Git & GitHub**

---

##  Database Table Structure

```sql
CREATE TABLE uploaded_files (
  id INT AUTO_INCREMENT PRIMARY KEY,
  file_name VARCHAR(255),
  file_content LONGBLOB
);
```

---

## Database Test Utility

A standalone Java class (`DBTest_Demo.java`) verifies both **MySQL** and **Oracle** remote database connections using a time-offset query for validation.

Usage:
```bash
java -jar DBTest.jar <hour_offset>
```

Example:
```bash
java -jar DBTest.jar 3
```

---

##  SSH and Configuration Commands

```bash
ssh -i "C:\Users\rshiw\Downloads\mysql_key.pem" ubuntu@3.143.247.27
```

Edit Apache config:
```bash
sudo nano /etc/apache2/sites-available/000-default.conf
```

Ensure reverse proxy setup forwards to Tomcat (usually port 8080).

---

## Project Structure Highlights

```
cs370_s25_FileUploadServlet/
├── src/
│   └── edu/cs/FileUploadServlet.java
│   └── edu/cs/DBTest_Demo.java
├── web/
│   └── index.html
├── pom.xml
└── target/
    └── cs370_s25fileuploadServlet-rahman-shiwlee.war
```

---

##  Notes

  sudo mv cs370_s25fileuploadServlet-rahman-shiwlee.war /opt/tomcat/webapps/
  sudo systemctl restart tomcat
  ```

---

## Instructor: Prof. Bon Sy  
**Course:** CS370 – Software Engineering  
**Semester:** Spring 2025  
**Student:** Shiwlee Rahman
