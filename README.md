# Cloud-Based Attendance Ingestion System  
(Azure VM | Nginx | Laravel | MySQL)

> This project was built as part of my **Microsoft Azure learning journey** using Microsoft Learn resources.  
> 🔗 **Microsoft Learn Contributor ID:** https://learn.microsoft.com/?wt.mc_id=studentamb_490811

---

## 📌 Project Overview
This project is a **VM-based backend attendance ingestion system** deployed on **Microsoft Azure**.

The system receives attendance data from attendance/biometric devices (or simulated clients) through a REST API and stores the data into a MySQL database.

This project focuses on **cloud deployment, Linux server administration, backend API handling, and database integration**.  

**The frontend and core application logic were not the focus of this project.**


---

## ☁️ Azure Infrastructure

- Hosted on Microsoft Azure Virtual Machine (Ubuntu Linux)
- Public IP exposed via Azure Networking
- Network Security Group configured for:
  - SSH (22)
  - HTTP (80)
  - HTTPS (443)
  - Attendance API (9000)
- Nginx used as reverse proxy on Azure VM



## 🧱 Architecture Overview (VM-Based)

Attendance Device / Client  
→ HTTP/HTTPS Request  
→ Nginx (Reverse Proxy)  
→ PHP-FPM  
→ Laravel REST API  
→ MySQL Database  

## **The entire setup runs on a **single Azure Linux Virtual Machine** for learning and demonstration purposes.**

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

Nginx is configured to listen on port 9000 to accept inbound HTTP requests from attendance devices.
The Laravel public directory is configured as the document root, while PHP request execution is handled by php8.4-fpm, ensuring proper separation between the web server and application runtime.


---

🔌 API Service Configuration

Service Endpoint

POST /api/adms/push

The endpoint is registered at the application layer and validated using:

php artisan route:list

This confirms that the API service is active and reachable from the web server.


---

Sample Request Payload

{
  "device_id": "DEVICE_01",
  "user_id": "EMP001",
  "timestamp": "2025-12-16 20:15:00",
  "status": "in"
}


---

Sample Service Response

{
  "status": "ok",
  "inserted": 1
}


---

🗄️ Data Storage (MySQL)

Database Name: mb460

Table Name: attendances


Attendance records received by the API service are written to the MySQL database.
Data persistence was verified directly at the database level.

Verification command:

SELECT COUNT(*) FROM attendances;


---

🧪 Service Testing & Health Verification

The API service was tested from the server side using curl to simulate requests from attendance devices:

curl -X POST http://127.0.0.1:9000/api/adms/push \
-H "Content-Type: application/json" \
-d '{
  "device_id": "DEVICE_01",
  "user_id": "EMP001",
  "timestamp": "2025-12-16 20:15:00",
  "status": "in"
}'

Operational health checks:

systemctl status nginx
systemctl status php8.4-fpm
php artisan route:list

These checks confirm that all required services are running and properly integrated.

🔐 Security & Networking Considerations
Azure Network Security Group (NSG) used to restrict inbound traffic
Only required ports are publicly exposed
HTTPS enabled using SSL/TLS
Reverse proxy architecture implemented using Nginx
Direct database access restricted to localhost
Backend services isolated from direct external access
---

📸 Operational Evidence

The screenshots/ directory contains the following verification artifacts:

API endpoint registration

Request processing and logs

MySQL attendance records

Nginx service status

HTTPS / SSL configuration status



---

✅ Operational Result

Attendance devices successfully connect to the API service

Requests pass through the web server and application runtime without errors

Attendance data is reliably stored in the database

The system operates stably on a Microsoft Azure Virtual Machine

🎓 Learning & Community Impact
This project was created to:
Practice real-world Azure VM deployments
Understand Linux-based backend service integration
Learn secure API exposure patterns
Share deployment and infrastructure knowledge with the learning community
The documentation and architecture are intentionally written to help beginners and junior engineers understand cloud-based backend systems.


---

📌 Notes

Application source code is intentionally kept private

Emphasis is placed on service configuration, integration, and operational stability

Project represents practical system and infrastructure engineering work rather than application development



---

👤 Author

Mosabbir Mridu
System & Cloud Engineer (Early Career)
Focused on Linux servers, service integration, and cloud infrastructure operations



