# Cloud-Based Attendance Ingestion System  
(Azure VM | Nginx | Laravel | MySQL)

---

## 📌 Project Overview
This project is a **VM-based backend attendance ingestion system** deployed on **Microsoft Azure**.

The system receives attendance data from attendance/biometric devices (or simulated clients) through a REST API and stores the data into a MySQL database.

This project focuses on **cloud deployment, Linux server administration, backend API handling, and database integration**.  
The frontend and core application logic were not the focus of this project.


---

## 🧱 Architecture Overview (VM-Based)

Attendance Device / Client  
→ HTTP/HTTPS Request  
→ Nginx (Reverse Proxy)  
→ PHP-FPM  
→ Laravel REST API  
→ MySQL Database  

The entire setup runs on a **single Azure Linux Virtual Machine** for learning and demonstration purposes.

---

## 🔧 Environment & Versions

| Component | Details |
|--------|--------|
| Cloud Platform | Microsoft Azure |
| VM OS | Ubuntu Linux |
| Web Server | Nginx |
| PHP | PHP 8.4 (PHP-FPM) |
| Backend Framework | Laravel |
| Database | MySQL 8.x |
| API Type | REST (JSON) |
| Security | HTTPS / SSL Enabled |

---

## ⚙️ Nginx Configuration (API Port)

The Laravel application is served using **Nginx + PHP-FPM**.

Key points:
- API listens on **port 9000**
- PHP handled via PHP-FPM socket
- Requests routed to `public/index.php`

Example (simplified):
```nginx
listen 9000;
root /var/www/mb460/public;
index index.php;
🔌 Laravel API Configuration
API Route
bash
Copy code
POST /api/adms/push
Registered using:

bash
Copy code
php artisan route:list
Sample JSON Payload
json
Copy code
{
  "device_id": "DEVICE_01",
  "user_id": "EMP001",
  "timestamp": "2025-12-16 20:15:00",
  "status": "in"
}
Sample API Response
json
Copy code
{
  "status": "ok",
  "inserted": 1
}
🗄️ Database Setup (MySQL)
Database: mb460

Table: attendances

Data insertion verified manually

Verification command:

sql
Copy code
SELECT COUNT(*) FROM attendances;
🧪 Testing & Verification
API tested using curl:

bash
Copy code
curl -X POST http://127.0.0.1:9000/api/adms/push \
-H "Content-Type: application/json" \
-d '{ ... }'
Other checks:

bash
Copy code
systemctl status nginx
systemctl status php8.4-fpm
php artisan route:list
📸 Proof of Work
Screenshots included:

API route list

API request logs

MySQL attendance data

Nginx service status

HTTPS / SSL verification

See the screenshots/ directory.

✅ Result
API endpoint successfully receives attendance data

Requests reach Laravel controller

Data is inserted into MySQL database

System runs reliably on Azure VM

📌 Notes
Source code is intentionally kept private

Project demonstrates cloud + backend infrastructure skills

Designed as a learning project for Azure / Linux / Backend fundamentals

👤 Author
Mosabbir Mridu
Beginner Cloud & System Engineer
Learning Azure, Linux, Backend APIs, and Infrastructure

