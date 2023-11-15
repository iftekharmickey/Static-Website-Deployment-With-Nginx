# Static Website Deployment with Nginx

This repository provides a comprehensive guide and code to deploy a static website using Nginx. Follow the step-by-step instructions below to set up your own static website effortlessly.

---

## Table of Contents

- [Static Website Deployment with Nginx](#static-website-deployment-with-nginx)
  - [Steps](#steps)
    - [1. Buy a Domain Name](#1-buy-a-domain-name)
    - [2. Spin up an Ubuntu Server](#2-spin-up-an-ubuntu-server)
    - [3. SSH into the Server and Install Nginx](#3-ssh-into-the-server-and-install-nginx)
    - [4. Download Website Files](#4-download-website-files)
    - [5. Copy Website Files to Nginx Directory Using SCP](#5-copy-website-files-to-nginx-directory-using-scp)
    - [6. Validate the Website Using Server IP](#6-validate-the-website-using-server-ip)
    - [7. Create A Record in DNS](#7-create-a-record-in-dns)
      - [Step-by-Step Guide to Creating an A Record](#step-by-step-guide-to-creating-an-a-record)
      - [Example Using Namecheap](#example-using-namecheap)
    - [8. Verify DNS Records Using `dig`](#8-verify-dns-records-using-dig)
    - [9. Verify Website Setup Using DNS](#9-verify-website-setup-using-dns)
    - [10. Create Let's Encrypt Certificate and Configure Nginx](#10-create-lets-encrypt-certificate-and-configure-nginx)
    - [11. Validate SSL Using OpenSSL](#11-validate-ssl-using-openssl)
  - [Note](#note)
  - [License](#license)

---

## Steps

### 1. Buy a Domain Name:

- Go to a domain registrar website (e.g., [Namecheap](https://www.namecheap.com/)).
- Purchase a domain name of your choice.

### 2. Spin up an Ubuntu Server:

- Choose a preferred cloud provider (e.g., AWS, DigitalOcean).
- Create an Ubuntu server instance.

### 3. SSH into the Server and Install Nginx:
```bash
ssh username@your_server_ip
sudo apt update
sudo apt install nginx
```

### 4. Download Website Files:
Find and download HTML files for your static website.

### 5. Copy Website Files to Nginx Directory Using SCP:
```bash
scp -r /path/to/your/local/website/* username@your_server_ip:/var/www/html/
```

### 6. Validate the Website Using Server IP:
- Open a web browser and enter your server's IP address.

### 7. Create A Record in DNS:
- Log in to your domain registrar account.
- Find the DNS settings.
- Create an A record pointing to your server's IP address.

### 8. Verify DNS Records Using `dig`:
```bash
dig your_domain.com
```

### 9. Verify Website Setup Using DNS:
- Open a web browser and enter your domain name.

### 10. Create Let's Encrypt Certificate and Configure Nginx:
```bash
sudo apt install certbot
sudo certbot --nginx -d your_domain.com
```

### 11. Validate SSL Using OpenSSL:
```bash
openssl s_client -connect your_domain.com:443
```

## Note
Make sure to replace `your_domain.com`, `your_server_ip`, and other placeholder values with your actual information.

---

## Step-by-Step Guide to Creating an A Record

1. **Log In to Your Domain Registrar Account:**
   - Go to the website of your domain registrar (e.g., Namecheap, GoDaddy, etc.).
   - Log in to your account using your credentials.

2. **Navigate to DNS Management or Domain Management:**
   - Find the section in your account dashboard related to DNS management or domain settings.

3. **Locate Your Domain:**
   - Locate the domain for which you want to create an A record.

4. **Access DNS Settings:**
   - Look for options like "DNS Settings," "Manage Domains," or "DNS Management." The terminology may vary.

5. **Add a New A Record:**
   - Within the DNS settings, find an option to add a new record.
   - Select "A" (Address) as the record type.

6. **Enter Details:**
   - You'll typically be prompted to enter the following details:
     
     - **Name/Host/Alias:** Leave it blank or enter `@` to indicate the root domain.
     - **Value/Points To/Destination:** Enter the IP address of your server.

7. **Save Changes:**
   - Save or apply the changes. This might involve clicking a "Save," "Add Record," or "Submit" button.

8. **Propagation Time:**
   - DNS changes may take some time to propagate across the internet. It could take a few minutes to several hours for the changes to take effect.

### Example Using Namecheap:

Here's an example using Namecheap:

1. Log in to your Namecheap account.
2. Navigate to the "Domain List" or "Manage Domains."
3. Find your domain and click on "Manage."
4. Look for the "Advanced DNS" or "DNS" tab.
5. Add a new A record with the server's IP address.
6. Save the changes.

---

## License
This project is licensed under the MIT License. See the [LICENSE](https://github.com/iftekharmickey/Static-Website-Deployment-With-Nginx/blob/main/LICENSE) file for details.
