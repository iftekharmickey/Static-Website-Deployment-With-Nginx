# Static Website Deployment with Nginx

This repository provides a comprehensive guide and code to deploy a static website using Nginx. Follow the step-by-step instructions below to set up your own static website effortlessly.

---

## Table of Contents

- [Static Website Deployment with Nginx](#static-website-deployment-with-nginx)
  - [Steps](#steps)
    - [1. Buy a Domain Name](#1-buy-a-domain-name)
    - [2. Spin up an Ubuntu Server](#2-spin-up-an-ubuntu-server)
       - [Step-by-Step Guide to Creating an Ubuntu Server Instance on AWS](#step-by-step-guide-to-creating-an-ubuntu-server-instance-on-aws)
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

## Step-by-Step Guide to Creating an Ubuntu Server Instance on AWS

1. **Sign in to AWS Console:**
   - Go to the [AWS Management Console](https://aws.amazon.com/).
   - Sign in to your AWS account.

2. **Navigate to EC2:**
   - In the AWS Management Console, navigate to the EC2 service.

3. **Launch an Instance:**
   - Click on the "Instances" link in the EC2 Dashboard.
   - Click the "Launch Instance" button.

4. **Choose an Amazon Machine Image (AMI):**
   - In the "Choose an Amazon Machine Image (AMI)" step, select an Ubuntu Server AMI. You can use the search bar to find the latest version of Ubuntu.

5. **Choose an Instance Type:**
   - In the "Choose an Instance Type" step, select the instance type that suits your needs. The default selection is usually a good starting point (e.g., t2.micro).

6. **Configure Instance:**
   - Click "Next: Configure Instance Details."
   - In this step, you can configure various settings such as the number of instances, network settings, and more. The default settings are often sufficient for a basic setup.

7. **Add Storage:**
   - Click "Next: Add Storage."
   - Configure the storage settings according to your requirements. The default settings are typically fine for a basic Ubuntu server.

8. **Add Tags (Optional):**
   - Click "Next: Add Tags" to add any tags if needed. Tags are useful for organizing and identifying instances.

9. **Configure Security Group:**
   - Click "Next: Configure Security Group."
   - Here, you define the rules that control traffic to your instance. At a minimum, you should allow SSH (port 22) for remote access.

10. **Review and Launch:**
    - Click "Review and Launch."
    - Review your instance configuration. If everything looks good, click "Launch."

11. **Create a Key Pair:**
    - In the "Select an existing key pair or create a new key pair" window, choose to create a new key pair.
    - Give your key pair a name, download it, and keep it in a secure location. This key pair is essential for SSH access to your instance.

12. **Launch Instances:**
    - Click "Launch Instances" to start your Ubuntu server.

### Accessing Your Ubuntu Server:

After the instance is launched, you can connect to it using SSH. Open a terminal on your local machine and use the following command:

```bash
ssh -i /path/to/your/key-pair.pem ubuntu@your_instance_ip
```

## Note
Replace `/path/to/your/key-pair.pem` with the path to your downloaded key pair file and `your_instance_ip` with the public IP address of your AWS instance.

---

## License
This project is licensed under the MIT License. See the [LICENSE](https://github.com/iftekharmickey/Static-Website-Deployment-With-Nginx/blob/main/LICENSE) file for details.
