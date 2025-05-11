# Windows Server Setup Documentation

## 1. Server Overview
- **Server Name:** SQLSERVER22
- **IP Address:** 192.168.1.58
- **OS:** Windows Server 2022 Standard
- **Installed Roles/Features:** Web Server (IIS), .NET Core Hosting Bundle

## 2. SQL Server Setup
- **Version:** SQL Server 2022 Standard
- **Instance Name:** SQLEXPRESS
- **Authentication:** Mixed Mode
- **Backup Path:** `C:\SQL\Bkups`
- **SSMS Installed:** Yes

## 3. ASP.NET Core Website Hosting
- **.NET Hosting Bundle Version:** 9.0.0
- **Sites Hosted:**
  - **Cellero Concrete DEV**: [https://cellero.vicmix.com.au:10443/](https://cellero.vicmix.com.au:10443/)
  - **Cellero Concrete DEV Mixes**: [https://cellero.vicmix.com.au:11443/](https://cellero.vicmix.com.au:11443/)
  - **Cellero Concrete PROD**: [https://cellero.vicmix.com.au:13443/](https://cellero.vicmix.com.au:13443/)
  - **Cellero Cloud Services PROD**: [https://cellero.vicmix.com.au:14443/](https://cellero.vicmix.com.au:14443/)
- **IIS App Pool Settings:**
  - No Managed Code
  - Identity: `ApplicationPoolIdentity`
- **Deployment:** Manual copy to `C:\inetpub\wwwroot`

## 4. Logging & Monitoring
- **IIS Logs:** `C:\inetpub\logs\LogFiles`
- **App Logs:** `C:\inetpub\wwwroot\AppName\Logs`
- **SQL Logs:** `C:\Program Files\Microsoft SQL Server\MSSQLXX.SQLEXPRESS\MSSQL\Log\`

## 5. Backup & Restore Procedures
- **Windows Schedule Task:** Daily at 11 PM

## 6. External Connectivity

### 6.1. Digital Matters
- **Internal URL:**  
  `https://cellero.vicmix.com.au:14443/api/app/ext-digital-matters-vehicles/vehicle-data`
  - **Method:** POST
  - **Purpose:** To receive vehicle data from the Digital Matters system.
  
  **Steps for Exposing the Endpoint Securely:**
  1. **Port Forwarding:**
     - Forward internal port `14443` to the external interface. Ensure that the router/firewall is configured to route requests to the internal server IP (e.g., `192.168.1.58:14443`).
  
  2. **Firewall Rules:**
     - **Incoming Firewall Rule (HTTPS):**  
       - Open port `14443` on the firewall to allow inbound traffic to the server. Ensure that the rule is restricted to allow only necessary traffic from trusted sources.
     - **Outbound Firewall Rule (HTTPS):**  
       - Allow outbound HTTPS traffic for any necessary external communications.

  3. **SSL Certificate Configuration:**
     - Ensure that the **SSL certificate** for `https://cellero.vicmix.com.au` is properly configured in IIS to ensure the endpoint is secure (TLS/SSL enabled).

  4. **External URL:**
     - The external URL will remain:  
       `https://cellero.vicmix.com.au:14443/api/app/ext-digital-matters-vehicles/vehicle-data`
     - This URL will allow secure communication with the external system, ensuring vehicle data is transferred securely via HTTPS.

---

### 6.2. Batch Plant Connections
Each batch plant is connected via **TCP/IP** protocol. Below is a list of the batch plants, their corresponding internal IPs, and ports:

| **Code** | **Name**      | **IP Address**  | **Port** |
|----------|---------------|-----------------|----------|
| COB      | COBURG        | 192.168.3.106   | 7000     |
| DAN      | DANDENONG     | 192.168.1.50    | 7000     |
| MOR      | MORNINGTON    | 192.168.4.24    | 7000     |
| PAK      | PAKENHAM      | 192.168.2.38    | 7000     |
| PK2      | PAKENHAM2     | 192.168.5.33    | 7000     |

**Steps for Exposing Each Batch Plant Connection Securely:**
1. **Port Forwarding:**
   - Forward the respective internal port (`7000`) for each batch plant to the external interface. Ensure that the router/firewall is configured to route requests to the internal IP of the corresponding batch plant (e.g., `192.168.3.106:7000` for COBURG).
  
2. **Firewall Rules:**
   - **Incoming Firewall Rule (TCP/IP):**  
     - Open port `7000` on the firewall to allow inbound traffic to each batch plant server. Ensure that the rule is restricted to allow only necessary traffic from trusted sources.
   - **Outbound Firewall Rule (TCP/IP):**  
     - Allow outbound TCP/IP traffic for any necessary external communications from the batch plant systems.

