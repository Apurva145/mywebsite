# AWS EC2 Website Hosting Project

## AIM

Amazon EC2 Configuration

1. Host a website on Windows EC2 instance
2. Host a website on Linux EC2 instance

---

# 1. Hosting Website on Windows EC2 Instance

## Step 1 — Login to AWS Console

- Login to your AWS account
- Open AWS Management Console

---

## Step 2 — Launch Windows EC2 Instance

1. Open EC2 Dashboard
2. Click **Launch Instance**
3. Enter Instance Name:
   ```bash
   host
   ```

4. Choose AMI:
   ```bash
   Microsoft Windows Server 2025 Base
   ```

5. Select Instance Type:
   ```bash
   t3.micro
   ```

6. Create Key Pair and download `.pem` file

7. Configure Network Settings

8. Configure Storage:
   ```bash
   30 GB SSD
   ```

9. Click:
   ```bash
   Launch Instance
   ```

---

## Screenshots

### AWS Login

### Launch Windows EC2 Instance

---

# Step 3 — Connect to Windows EC2 Instance

1. Select running instance
2. Click:
   ```bash
   Connect
   ```

3. Choose:
   ```bash
   RDP Client
   ```

4. Download Remote Desktop File
5. Click:
   ```bash
   Get Password
   ```

6. Upload `.pem` file
7. Click:
   ```bash
   Decrypt Password
   ```

---

# Step 4 — Remote Desktop Connection

1. Open Run:
   ```bash
   Win + R
   ```

2. Type:
   ```bash
   mstsc.exe
   ```

3. Enter Public IP Address
4. Login using:
   ```bash
   Username: Administrator
   ```

5. Paste decrypted password
6. Click OK

---

# Step 5 — Install IIS Web Server

1. Open:
   ```bash
   Server Manager
   ```

2. Click:
   ```bash
   Add Roles and Features
   ```

3. Select:
   ```bash
   Web Server (IIS)
   ```

4. Click Install

---

## Verify IIS Installation

Open browser inside Windows Server:

```bash
http://localhost
```

Default IIS page should appear.

---

# Step 6 — Configure Security Group

| Type | Port | Source |
|------|------|------|
| RDP | 3389 | My IP |
| HTTP | 80 | 0.0.0.0/0 |

---

# Step 7 — Deploy Custom Website

Navigate to:

```bash
C:\inetpub\wwwroot
```

- Delete default IIS files
- Copy custom website files

Restart IIS:

```bash
iisreset
```

---

# Step 8 — Verify Website

Open browser:

```bash
http://<Public-IP>
```

Custom website should display successfully.

---

# 2. Hosting Website on Linux EC2 Instance

## Step 1 — Login to AWS Console

Login to AWS account.

---

# Step 2 — Launch Linux EC2 Instance

1. Open EC2 Dashboard
2. Click:
   ```bash
   Launch Instance
   ```

3. Enter Instance Name:
   ```bash
   host
   ```

4. Choose AMI:
   ```bash
   Amazon Linux 2023
   ```

5. Select Instance Type:
   ```bash
   t3.micro
   ```

6. Create Key Pair and download `.pem` file

7. Configure Network Settings

8. Configure Storage:
   ```bash
   30 GB SSD
   ```

9. Click:
   ```bash
   Launch Instance
   ```

---

# Step 3 — Connect to Linux EC2 Instance

1. Select instance
2. Click:
   ```bash
   Connect
   ```

3. Use:
   ```bash
   EC2 Instance Connect / SSH
   ```

---

# Step 4 — Update System Packages

Run:

```bash
sudo dnf update -y
```

---

# Step 5 — Install Apache Web Server

Run:

```bash
sudo dnf install httpd -y
```

---

# Step 6 — Start and Enable Apache

Start Apache:

```bash
sudo systemctl start httpd
```

Enable Apache:

```bash
sudo systemctl enable httpd
```

Check Status:

```bash
sudo systemctl status httpd
```

Expected Result:

```bash
active (running)
```

---

# Step 7 — Configure Security Group

| Type | Port | Source |
|------|------|------|
| SSH | 22 | My IP |
| HTTP | 80 | 0.0.0.0/0 |

---

# Step 8 — Test Apache Server

Open browser:

```bash
http://<Public-IP>
```

Apache default page should appear.

---

# Step 9 — Create Custom Web Page

Navigate to web directory:

```bash
cd /var/www/html
```

Remove default page:

```bash
sudo rm -f index.html
```

Create new HTML file:

```bash
sudo nano index.html
```

Add custom HTML code and save.

---

# Step 10 — Verify Custom Website

Refresh browser:

```bash
http://<Public-IP>
```

Custom webpage should display successfully.

---

# Technologies Used

- AWS EC2
- Windows Server
- Linux Server
- IIS Web Server
- Apache Web Server
- HTML
- CSS

---

# Author

## Apurva Patel

Department of Computer Engineering

Ganpat University
