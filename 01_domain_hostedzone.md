# 01_domain_hostedzone.md

## Domain Purchase and Hosted Zone Setup

1. **Purchased Domain**  
   - Domain Name: `donjo.space`  
   - Purchased from: **Hostinger**

2. **Hostinger Name Servers**  
   - Hostinger provided 4 default name servers for the domain.

3. **AWS Route 53 Hosted Zone**  
   - Created a **Hosted Zone** in **AWS Route 53** with the same domain name: `donjo.space`.  
   - Route 53 provided 4 NS (Name Server) records.

4. **Updating Name Servers in Hostinger**  
   - Copied the 4 NS records from Route 53.  
   - Updated the domain’s NS records in Hostinger with the Route 53 NS.  
   - This effectively delegates DNS management to Route 53.

5. **Result**  
   - Domain `donjo.space` is now pointing to AWS Route 53 for DNS management.
<img width="1037" height="565" alt="image" src="https://github.com/user-attachments/assets/a872b412-36de-453a-b3c1-00884454095c" />
<img width="905" height="432" alt="image" src="https://github.com/user-attachments/assets/58c12953-f4e5-44de-ac58-ec3ad68fdf51" />

