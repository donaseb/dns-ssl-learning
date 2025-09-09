# Hosting `donjo.space` on AWS EC2 with Elastic IP and Route 53 (Ubuntu Apache Setup)

This document outlines the steps taken to host the domain `donjo.space` on an EC2 instance using an Elastic IP and Route 53, and how the web server was configured on Ubuntu to make it accessible via browser.

---

## 1. Elastic IP Allocation

* Allocated an **Elastic IP** for the EC2 instance.
* Ensures the EC2 instance has a **static public IP** for the domain.
  <img width="1063" height="266" alt="image" src="https://github.com/user-attachments/assets/cbf303de-fbef-4595-8a18-8309b67610b9" />


---

## 2. Route 53 DNS Setup

###A Record Creation

Record Name: donjo.space

Type: A (IPv4 address)

Value: <Elastic IP> (the static IP allocated to your EC2 instance)

TTL: Default (e.g., 300 seconds)

Purpose:

-Maps the root domain donjo.space to the EC2 instance.

-Ensures that requests to donjo.space reach your EC2 instance
  

donjo.space → 3.6.152.26

- Verified DNS resolution with:
 ```bash
nslookup donjo.space
```
<img width="642" height="269" alt="image" src="https://github.com/user-attachments/assets/b8e28ec1-a2f3-4540-81e9-24d0cf83d1e0" />




Output: Elastic IP address of the EC2 instance.

---

## 3. Apache Web Server Configuration on Ubuntu

Since the site was not accessible via the domain initially, the Apache web server was configured.

1. **Edit the default virtual host file**:

```bash
sudo vim /etc/apache2/sites-available/000-default.conf
```

2. **Add/update the `<VirtualHost>` block**:

```apache
<VirtualHost *:80>
    ServerName donjo.space
    DocumentRoot /var/www/html
</VirtualHost>
```

**Explanation:**

* `<VirtualHost *:80>` → Handles all HTTP requests on port 80 for any IP on the server.
* `ServerName donjo.space` → Ensures Apache serves this configuration when someone accesses `donjo.space`.
* `DocumentRoot /var/www/html` → Specifies the folder where website files (like `index.html`) are stored.

3. **Enable the site (usually already enabled by default)**:

```bash
sudo a2ensite 000-default.conf
```

4. **Restart Apache to apply changes**:

```bash
sudo systemctl restart apache2
```

---

## 4. Verification

* Open browser and navigate to:

```
http://donjo.space
```

* The site should load successfully.

---
<img width="1758" height="767" alt="image" src="https://github.com/user-attachments/assets/65646cab-5b8d-4f52-9bbd-55d57f89cf09" />


✅ **Result:**
The EC2 instance is now reachable via the domain `donjo.space` using the Elastic IP and properly configured Apache web server on Ubuntu.
