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
