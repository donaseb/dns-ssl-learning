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

``` bash
sudo service apache2 restart
```
<img width="1917" height="910" alt="image" src="https://github.com/user-attachments/assets/a6801609-5e69-478e-9030-ee137998868c" />






