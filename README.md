# Project: Mofiyinfoluwa’s Landing Page

The project, **"Mofiyinfoluwa’s Landing Page"**, is a demonstration of deploying a static web page on an Apache web server hosted on an AWS EC2 instance. This project highlights the following key skills and configurations:
- Create and configure a server (Linux) environment.
- Installing and configuring the Apache web server.
- Deploying a custom HTML page.
- Securing the web server with SSL certificates using Certbot for HTTPS access.

The deployed landing page is designed to introduce the creator and also provide relevant project details. To replicate the setup of this project, please follow the steps outlined below:

## 1. Create and Configure the Server Instance

### Launch an instance:
- Navigate to your cloud provider's console (I used AWS Management Console).
- Click **Launch Instance**.
- Name your instance for identification.
- Choose an AMI (Amazon Machine Image): For example, Ubuntu 22.04 LTS, Amazon Linux 2, etc. (I chose Ubuntu 24.04) for the server.
- Select an instance type: Example: `t2.micro` (free tier eligible).
- Configure a key pair: If you don’t have one, create a new one and download the `.pem` file. (This file is essential for connecting to your EC2 instance via SSH.)
- Set security group rules:
  - Allow port 22 (SSH) for remote access.
  - Allow port 80 (HTTP) and port 443 (HTTPS) if hosting a web server.
- Review and launch your instance.

### Connect to your instance and access the server via SSH:
- After launching the instance, select the instance and click **Connect**.
- Log on to your terminal and use SSH to access the server by running the following command:
  ```bash
  ssh -i /path/to/your-key.pem username@your-server-ip
2. Installing and Configuring Apache Web Server
Update the Server:
First, ensure the server is up to date by running the update command: For Ubuntu/Debian:

bash
Copy code
sudo apt update
sudo apt upgrade -y
Install Apache Web Server:
For Ubuntu/Debian:

bash
Copy code
sudo apt install apache2 -y
Start Apache Web Server:
For Ubuntu/Debian:

bash
Copy code
sudo systemctl start apache2
sudo systemctl enable apache2
Verify Apache Installation:
Open a web browser and navigate to the server’s IP address (e.g http://52.207.137.118). If Apache is installed correctly, you should see the default Apache welcome page.

3. Deploying the HTML Page
Create an HTML Page:
 On your local machine, create an HTML file (e.g., index.html) with your content:(I created this before launching the instance)

html
Copy code
<html>
  <head><title>My Landing Page</title></head>
  <body>
    <h1>Welcome to My Landing Page!</h1>
  </body>
</html>
Upload the HTML Page to the Server:
Use SCP (Secure Copy) to transfer the HTML file to the server by running this command on your terminal:

bash
Copy code
scp index.html username@your-server-ip:/var/www/html/
Verify HTML Deployment:
In your web browser, go to the server’s IP address again (e.g., http://your-server-ip). Your custom HTML page should now be displayed instead of the default Apache page.

Check Firewall Configuration:
For Ubuntu/Debian (UFW):

bash
Copy code
sudo ufw status
Allow HTTP Traffic Through Firewall:
For Ubuntu/Debian (UFW):

bash
Copy code
sudo ufw allow 'Apache Full'
Check Apache’s Listening Ports:
Ensure Apache is listening on port 80:

bash
Copy code
sudo netstat -tulnp | grep apache
Verify Public Accessibility:
Ensure the server’s public IP is accessible from external devices. In your browser, enter http://your-server-ip to check if the server is reachable.

4. Securing the Web Server with SSL Certificates Using Certbot for HTTPS Access
Set Up SSL (Secure HTTPS):
Install Certbot to enable SSL for Apache and secure the server: For Ubuntu/Debian:

bash
Copy code
sudo apt install certbot python3-certbot-apache -y
Obtain and Configure an SSL Certificate for Your Domain:
bash
Copy code
sudo certbot --apache -d web.mofiyinfoluwa.crabdance.com
Follow the prompts to configure SSL and secure your site with HTTPS.

Optimize Apache:
For Ubuntu/Debian:

Edit /etc/apache2/apache2.conf
Verify Setup:
Open a browser and navigate to confirm the secure connection. To access my landing page, click on https://web.mofiyinfoluwa.crabdance.com/

The public ip address obtained when i launched the instance is 52.207.137.118


