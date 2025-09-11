## we will discuss how to enable https for your website hosted on ubuntu ( For Testing purpose)
### Step 1 - Install Let's Encrypt
Execute the following commands to install Let's Encrypt on Ubuntu:
``` bash
sudo apt install certbot python3-certbot-apache
```
### Step 2 - Allow HTTPS through the firewall and configure Apache2 virtual hosts
If you are using Apache, enter the following commands to allow Apache2 over the firewall:
``` bash
sudo ufw allow 'Apache Full'
```
### Step 3 - Obtain an SSL certificate
Run the following command to obtain an SSL certificate:
``` bash
sudo certbot --apache
```
<img width="865" height="260" alt="image" src="https://github.com/user-attachments/assets/cc1dbefe-c663-4f73-b450-de9e583783d8" />  
<img width="1028" height="188" alt="image" src="https://github.com/user-attachments/assets/9dc8676b-86e8-49e5-8b79-f5f0d74dc685" />  
<img width="1205" height="433" alt="image" src="https://github.com/user-attachments/assets/39a5726f-1450-472f-9e18-1d273c1eba38" />  
<img width="1205" height="433" alt="image" src="https://github.com/user-attachments/assets/5bc25ac3-dbc9-4352-80bb-aa8065d0f9d8" />  

### Step 4 :Restart:
``` bash
sudo service apache2 restart
```
<img width="1917" height="910" alt="image" src="https://github.com/user-attachments/assets/a6801609-5e69-478e-9030-ee137998868c" />

## Installing server certificates manually in IIS
### Using IIS Manager:

- On the IIS Manager at the server level, locate the “Server Certificates” icon and double-click it

<img width="1067" height="400" alt="image" src="https://github.com/user-attachments/assets/a98ddbe8-6518-4e7d-a431-717209615710" />

- Locate the “Actions” pane on the ride side and click “Import”
- This will open up the Import dialog box

  <img width="586" height="509" alt="image" src="https://github.com/user-attachments/assets/7c781e3e-2651-4e8b-81a0-f0dc0dcfda9b" />
- Provide the .pfx file full path, password for the keys and click OK. This will install the certificate for you
## Manually importing an SSL certificate on an Ubuntu server 
- Manually importing an SSL certificate on an Ubuntu server involves several steps, assuming you have the certificate files (private key, server certificate, and potentially intermediate/CA bundle) already issued by a Certificate Authority (CA)
#### 1. Prepare Certificate Files:
- Ensure you have your private key (.key), the server certificate (.crt), and any intermediate certificates or CA bundle (.crt or .ca-bundle) provided by your CA.
#### 2. Copy Certificate Files to Server:
- Transfer these files to a secure location on your Ubuntu server. A common practice is to create a dedicated directory within /etc/ssl/ or /etc/apache2/ssl/ (if using Apache). For example:
``` bash
    sudo mkdir -p /etc/ssl/my_domain
    sudo cp /path/to/your/certificate.crt /etc/ssl/my_domain/
    sudo cp /path/to/your/private.key /etc/ssl/my_domain/
    sudo cp /path/to/your/ca-bundle.crt /etc/ssl/my_domain/
```
- Important: Set appropriate permissions for your private key to prevent unauthorized access:
  ``` bash
      sudo chmod 600 /etc/ssl/my_domain/private.key
  ```
#### 3. Configure your Web Server (e.g., Apache):
- Enable the SSL module, if not already enabled
``` bash
  sudo a2enmod ssl
```
- Open the SSL virtual host file for your domain. Configuration files are typically located in /etc/apache2/sites-available/ and enabled by a symbolic link in /etc/apache2/sites-enabled/.
``` bash
sudo nano /etc/apache2/sites-available/your_domain.conf
```
- Find the <VirtualHost> block for port 443 (or create one if it doesn't exist) and update the certificate paths
``` bash
<VirtualHost *:443>
    ServerName www.your_domain.com
    DocumentRoot /var/www/your_domain_root
    SSLEngine on
    SSLCertificateFile /etc/ssl/certs/your_domain.crt
    SSLCertificateKeyFile /etc/ssl/private/your_domain.key
    SSLCertificateChainFile /etc/ssl/certs/ca_bundle.crt
</VirtualHost>
```
- Save the file and check the configuration for syntax errors
``` bash
sudo apache2ctl configtest
```
- Restart Apache for the changes to take effect
``` bash
sudo systemctl restart apache2
```

  



