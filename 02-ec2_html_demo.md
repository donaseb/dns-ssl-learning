# 02\_ec2\_demo\_app.md

## Launch EC2 and Host a Simple Web App

### 1. Launch an EC2 Instance

* **Instance Type:** `t2.micro`
* **AMI:** Ubuntu (latest LTS)
* **Key Pair:** Use your existing key pair or create a new one
* **Security Group:** Allow inbound HTTP (port 80),HTTPS traffic (port 443) and SSH (port 22)

### 2. Connect to EC2

```bash
ssh -i ~/Downloads/your-key.pem ubuntu@<EC2_PUBLIC_IP>
```

### 3. Install a Web Server

```bash
sudo apt update
sudo apt install -y apache2
sudo systemctl start apache2
sudo systemctl enable apache2
```

### 4. Create a Simple Index Page

### 1. SSH into EC2

```bash
ssh -i C:\Users\user1\Downloads\your-key.pem ubuntu@<EC2_PUBLIC_IP>
```

### 2. Open `index.html` in Vim

```bash
sudo vim /var/www/html/index.html
```

* Press `i` to enter **Insert mode**.

### 3. Copy and Paste HTML Content

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hello World</title>
    <style>
        body {
            background-color: #f4f4f9;
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 20%;
        }
        h1 {
            color: #333;
            font-size: 3rem;
        }
    </style>
</head>
<body>
    <h1>Hello, World! 👋</h1>
</body>
</html>
```

### 4. Save and Exit Vim

* Press `Esc` to return to Normal mode.
* Type:

```
:wq
```

### 5. Set Correct Permissions

```bash
sudo chown www-data:www-data /var/www/html/index.html
sudo chmod 644 /var/www/html/index.html
```

### 6. Test the Page

* Visit in browser: `http://<EC2_PUBLIC_IP>` 



