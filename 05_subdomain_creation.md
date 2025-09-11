# Subdomain Creation and Delegation in Route 53

This guide explains how to create and delegate subdomains for the root domain **donjo.space** using AWS Route 53.

---
## 1. Subdomain Creation (Example: `app.donjo.space`)

1. Go to the **Route 53 Console**.
2. Select your hosted zone for **donjo.space**.
3. Click **Create record**.
4. Add a record for the subdomain:
   - **Record name**: `app`
   - **Record type**: `A`
   - **Value**: Public IP of your EC2 instance (e.g., `13.233.xxx.xxx`)
   - **TTL**: Default (300 seconds)

✅ Now, visiting `http://app.donjo.space` will point to your EC2 instance.

---
## 2. Subdomain Delegation (Example: `dev.donjo.space`)
Sometimes, you may want a subdomain (`dev.donjo.space`) to be managed by a separate hosted zone.  
This is called **delegation**.
### Step 1: Create a Hosted Zone for the Subdomain
1. Go to **Route 53 → Hosted zones**.
2. Click **Create hosted zone**.
3. Enter:
   - **Domain name**: `dev.donjo.space`
   - **Type**: Public hosted zone
4. Note down the **NS (Name Server) records** that AWS provides for this zone.
<img width="1214" height="720" alt="image" src="https://github.com/user-attachments/assets/57531a23-6f15-46f2-8234-30ba42578e1f" />

---
### Step 2: Add NS Records in Parent Zone
1. Go back to your **root hosted zone** (`donjo.space`).
2. <img width="1080" height="406" alt="image" src="https://github.com/user-attachments/assets/927a79e9-5f4f-4006-a1e6-fe5c5e3a63be" />
2 Click **Create record**.
4. Add:
   - **Record name**: `dev`
   - **Record type**: `NS`
   - **Value**: Paste the NS values from the `dev.donjo.space` hosted zone.

<img width="1081" height="747" alt="image" src="https://github.com/user-attachments/assets/e1307564-6baa-414c-8859-c88095e86b9b" />
<img width="1075" height="766" alt="image" src="https://github.com/user-attachments/assets/763aae72-6c85-4aa1-8705-76cbe66d8128" />
<img width="819" height="500" alt="image" src="https://github.com/user-attachments/assets/cf311ca9-915c-44ad-bf1e-90b3b6fddf34" />




✅ Now, all DNS queries for `dev.donjo.space` will be handled by the new hosted zone.

---
## 3. Example Use Cases
- `app.donjo.space` → Points directly to an EC2 instance (simple subdomain creation).
- `dev.donjo.space` → Delegated to another hosted zone for team/project separation.

---
## 4. Cost Notes
- Subdomains (`app.donjo.space`, `api.donjo.space`, etc.) are **free** once you own the root domain.
- You only pay for:
  - The root domain (`donjo.space`)
  - Hosted zones in Route 53
  - The infrastructure (EC2, S3, etc.) that the subdomain points to

---
