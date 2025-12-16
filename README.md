# Cloud-Based Attendance Ingestion System (Azure + Laravel)

## 📌 Project Overview
This project is a **cloud-hosted attendance data ingestion system** designed to receive raw attendance data from biometric / attendance devices and store it securely in a centralized database.

The system is deployed on **Microsoft Azure VM**, uses **Nginx + PHP-FPM**, and is built with **Laravel (API-based architecture)**.

It demonstrates real-world skills in:
- Cloud infrastructure
- Secure API design
- Backend data processing
- Linux server administration

---

## 🧱 Architecture Overview

Device / Client  
→ HTTPS API (Nginx)  
→ Laravel API Controller  
→ MySQL Database  
→ Logs & Monitoring

---

## 🚀 Features
- REST API endpoint to receive attendance data
- Supports JSON-based device payloads
- Laravel API routing & controller handling
- MySQL database storage
- SSL-enabled (HTTPS)
- Deployed on Azure Virtual Machine
- Nginx reverse proxy with PHP-FPM

---

## 🔗 API Endpoint

POST /api/adms/push


### 📥 Sample Request Payload
```json
{
  "device_id": "DEVICE_01",
  "user_id": "EMP001",
  "timestamp": "2025-12-16 20:15:00",
  "status": "in"
}

📤 Sample API Response
{
  "status": "ok",
  "inserted": 1
}

🛠 Technology Stack

Cloud Platform: Microsoft Azure (Virtual Machine)

Operating System: Ubuntu Linux

Web Server: Nginx

Backend Framework: Laravel (PHP 8.4)

Database: MySQL

Security: SSL / HTTPS

Tools: curl, systemctl, Laravel Artisan


📂 Project Structure (Simplified)
attendance-cloud-project/
├── screenshots/
│   ├── route-list-api.png
│   ├── api-log.png
│   ├── mysql-data.png
│   ├── nginx-running.png
│   ├── ssl-enabled.png
├── README.md

📸 Proof of Work (Screenshots)
Description	Screenshot
Laravel API Route Registered	screenshots/route-list-api.png
API Request Logged	screenshots/api-log.png
Attendance Data Stored in MySQL	screenshots/mysql-data.png
Nginx Service Running	screenshots/nginx-running.png
HTTPS / SSL Enabled	screenshots/ssl-enabled.png

🔍 Verification Commands

php artisan route:list | grep adms
curl -X POST http://127.0.0.1:9000/api/adms/push
systemctl status nginx
systemctl status php8.4-fpm
mysql -u mb460user -p

📈 What This Project Demonstrates

Real-world cloud server deployment

REST API design and testing

Linux server management

Secure backend configuration (SSL)

Database connectivity and validation

Production-style troubleshooting

👤 Author

Mosabbir Mridu
Aspiring Cloud & System Engineer
Focused on Azure, Linux, Backend APIs, and Infrastructure

📌 Note

Source code is intentionally kept private.
This repository demonstrates deployment architecture, API behavior, and operational proof without exposing proprietary application code.
