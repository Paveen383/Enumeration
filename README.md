## NAME: PAVEEN KUMARAN SV
## REG. NO.: 212224220071
## DATE: 31/01/2026

# Explore Google hacking and enumeration 

# AIM:

To use Google for gathering information and perform enumeration of targets

## STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various Google hacking keywords and enumeration tools as follows:


### Step 3:
Open terminal and try execute some kali linux commands

## Pen Test Tools Categories:  

| Operator    | Description                        | Example Usage           |
| ----------- | ---------------------------------- | ----------------------- |
| `site:`     | Search within a specific domain    | `site:example.com`      |
| `inurl:`    | Search in URL                      | `inurl:admin`           |
| `intitle:`  | Search in page title               | `intitle:"index of"`    |
| `filetype:` | Search by file type                | `filetype:pdf`          |
| `intext:`   | Search inside page text            | `intext:"confidential"` |
| `link:`     | Pages that link to a specific site | `link:example.com`      |
| `cache:`    | View cached version of a site      | `cache:example.com`     |
| `ext:`      | Same as filetype                   | `ext:xls`               |

 ## Architecture 
 ```
+----------------------+
|   Attacker / Hacker  |
|   (Browser & Google) |
+----------+-----------+
           |
           | Google Dork Queries
           v
+---------------------------+
|       Google Search       |
+---------------------------+
           |
           | Indexed Public Content
           v
+---------------------------+
|   Target Websites / Data  |
| - Leaked files            |
| - Open directories        |
| - Sensitive info          |
+---------------------------+

```

# Output:
SITE:
<img width="1919" height="1079" alt="Screenshot 2026-01-31 133325" src="https://github.com/user-attachments/assets/9df261eb-07e6-49aa-aaa5-a8845010e33f" />


INURL:
<img width="1919" height="1079" alt="Screenshot 2026-01-31 133800" src="https://github.com/user-attachments/assets/b488f777-ded3-4fa9-8182-4eaef9307086" />


INTITLE:
<img width="1917" height="1079" alt="image" src="https://github.com/user-attachments/assets/1760e27b-9fb1-45b7-b680-d83133e48b97" />


FILETYPE.PDF
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/f06f6b33-119a-4db2-a8c0-a708256e7a97" />


INTEXT:
<img width="1917" height="1070" alt="image" src="https://github.com/user-attachments/assets/7a98f844-4e79-42f5-b2b9-1a64f786466d" />


LINK:
<img width="1918" height="1079" alt="image" src="https://github.com/user-attachments/assets/dfa8023e-20ed-40a2-a51d-bf84cecd6305" />


CACHE:
<img width="1919" height="1034" alt="Screenshot 2025-08-30 155023" src="https://github.com/user-attachments/assets/badeb877-1507-49a3-9090-feef48eaebdf" />


# DNS Enumeration
<img width="1916" height="1079" alt="image" src="https://github.com/user-attachments/assets/2c4f58fd-415a-4a01-a213-217094d4c1f1" />



## DNS Recon

| Record Type | Meaning                        | Example Output                   |
| ----------- | ------------------------------ | -------------------------------- |
| A           | Host to IPv4 address           | `example.com -> 93.184.216.34`   |
| AAAA        | Host to IPv6 address           | `example.com -> ::1`             |
| MX          | Mail server info               | `mail.example.com`               |
| NS          | Name servers                   | `ns1.example.com`                |
| TXT         | Misc data (SPF, verifications) | `v=spf1 include:_spf.google.com` |
| CNAME       | Canonical names (aliases)      | `www -> example.com`             |

## Common Tools Used (Kali Linux)

| Tool           | Description                                | Usage Example                           |
| -------------- | ------------------------------------------ | --------------------------------------- |
| `nslookup`     | DNS lookup tool (simple queries)           | `nslookup example.com`                  |
| `dig`          | DNS lookup utility (detailed)              | `dig example.com any`                   |
| `host`         | Simple DNS querying tool                   | `host example.com`                      |
| `dnsenum`      | Perl script to enumerate DNS info          | `dnsenum example.com`                   |
| `fierce`       | DNS scanner to locate non-contiguous IPs   | `fierce -dns example.com`               |
| `dnsrecon`     | Powerful DNS enumeration script            | `dnsrecon -d example.com -a`            |
| `theHarvester` | Subdomain enumeration using search engines | `theHarvester -d example.com -b google` |


## OUTPUT:

### NSLOOKUP:
<img width="1919" height="1065" alt="image" src="https://github.com/user-attachments/assets/2ecf259b-979e-4c48-bb20-177fdf67851b" />



### DIG:
<img width="1917" height="1079" alt="image" src="https://github.com/user-attachments/assets/65b53e7c-a88e-49c2-9d98-d8c7aee2189e" />



### HOST:
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/a265dc72-915f-447c-bec6-21bb450352ad" />



### DNSENUM:
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/463bc99f-b35e-493a-945f-efa197660ac4" />
 

### FIERCE:

<img width="1919" height="1079" alt="Screenshot 2026-01-31 142058" src="https://github.com/user-attachments/assets/9863dde5-b03d-4460-bc36-7e92560d9e81" />


### theHarvester:
<img width="1912" height="1073" alt="Screenshot 2026-01-31 141912" src="https://github.com/user-attachments/assets/167a75c0-bc86-4938-9ee0-2fcbc15b300b" />

## Architecture Diagram 
```
+-------------------+        +------------------+       +------------------+
|                   |        |                  |       |                  |
|   Attacker (You)  +------->|   Target Server   +<----->+    DNS Server    |
| Kali Linux / Parrot|       | (Mail / DNS Host) |       |  (Authoritative) |
+---------+---------+        +---------+--------+       +---------+--------+
          |                            ^                          ^
          |                            |                          |
          |                            |                          |
          |           +-----------------------------+            |
          |           |      Information Tools      |            |
          |           |-----------------------------|            |
          |           | smtp-user-enum              |            |
          |           | nmap --script smtp-enum-*   |            |
          |           | dnsenum                     |<-----------+
          |           +-----------------------------+
          |
          v
+-----------------------------+
|   Output/Report             |
|  - Usernames Found          |
|  - MX Records / Zones       |
|  - Subdomains / IPs         |
+-----------------------------+

```

## dnsenum
**Purpose:** A multithreaded Perl script to enumerate information from DNS servers.

**Use case:** Performs DNS zone transfers, brute force subdomains, and gather host IPs.

```
dnsenum example.com
```

## Output:

<img width="1919" height="1065" alt="Screenshot 2026-01-31 140457" src="https://github.com/user-attachments/assets/d340f3f5-c3a7-4ebe-8406-d192df40a7e1" />


## smtp-user-enum
**Purpose:** Standalone tool used to enumerate valid users by using the VRFY, EXPN, or RCPT TO commands.

**Use case:** Brute-forces SMTP to find users.

```
smtp-user-enum -M VRFY -U users.txt -t <target-ip>
```
  
 ## Output

<img width="1919" height="1079" alt="Screenshot 2026-01-31 142058" src="https://github.com/user-attachments/assets/e2839069-4b27-4cbc-af57-c695f57dd90b" />



## nmap –script smtp-enum-users.nse <hostname>

**Purpose:** Uses smtp-enum-users NSE script to enumerate valid users on an SMTP server.

**Use case:** Helps identify email accounts on mail servers.

```
nmap -p 25 --script smtp-enum-users.nse <target-ip>
```
## OUTPUT:

<img width="1915" height="1075" alt="image" src="https://github.com/user-attachments/assets/9b02375d-4fae-4a17-b83c-d4c35a5b0fd6" />


## RESULT:
The Google hacking keywords and enumeration tools were identified and executed successfully
