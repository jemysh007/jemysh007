Sure! Here's the updated README with **Step 0** for logging into the server via SSH.

---

# Hosting a Node.js Project from GitHub on Ubuntu Server with Nginx Server, PM2, `yourdomain.in` Domain, SSL

This guide walks you through the steps to host a Node.js project from a GitHub repository on an Ubuntu server, use PM2 for process management (with a custom project name), configure the domain **yourdomain.in** for accessing the application, and enable SSL using **Let's Encrypt** for secure HTTPS access.

## Prerequisites

- A blank Ubuntu server (Ubuntu 20.04 or later).
- SSH access to the server.
- A GitHub repository containing your Node.js project.
- A domain name **yourdomain.in** pointing to your server’s IP.
- Basic knowledge of using the command line.

## Step 0: SSH Login to the Server

To log in to your Ubuntu server via SSH, use the following command. Replace `your-server-ip` with the IP address of your server, and `your-username` with your username (e.g., `ubuntu` or `root`):

```bash
ssh your-username@your-server-ip
```

For example:

```bash
ssh ubuntu@192.168.1.1
```

If you're using an SSH key for authentication, make sure to specify the private key file with the `-i` option:

```bash
ssh -i /path/to/your/private-key.pem your-username@your-server-ip
```

## Step 1: Update and Upgrade the System

Before starting, make sure the server is up-to-date.

```bash
sudo apt update && sudo apt upgrade -y
```

## Step 2: Install Node.js and npm

1. **Install Node.js**

   To install the latest LTS version of Node.js, run the following commands:

   ```bash
   curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
   sudo apt install -y nodejs
   ```

2. **Verify Installation**

   Check the installed versions of Node.js and npm.

   ```bash
   node -v
   npm -v
   ```

## Step 3: Install PM2

PM2 is a process manager that helps you keep your Node.js application running in the background.

1. **Install PM2 globally**

   ```bash
   sudo npm install -g pm2
   ```

2. **Verify PM2 Installation**

   ```bash
   pm2 -v
   ```

## Step 4: Clone Your Node.js Project from GitHub

1. **Install Git (if not already installed)**

   ```bash
   sudo apt install git
   ```

2. **Clone the Project Repository**

   Replace `your-repository-url` with the URL of your GitHub repository (e.g., `https://github.com/username/your-project.git`).

   ```bash
   git clone https://github.com/username/your-project.git
   ```

3. **Navigate to Your Project Directory**

   ```bash
   cd your-project
   ```

4. **Install Project Dependencies**

   If your project has a `package.json` file, install the required dependencies:

   ```bash
   npm install
   ```

## Step 5: Run the Node.js Application with PM2

Now that your project is set up, start it using PM2.

1. **Start Your Application with PM2**

   Assuming your entry file is `app.js`, run:

   ```bash
   pm2 start app.js --name "your-app-name"
   ```

   Replace `"your-app-name"` with a name for your PM2 process (e.g., `"jemish-app"`). This helps you identify and manage the application more easily in PM2.

2. **Verify the Application is Running**

   To check the status of your Node.js app:

   ```bash
   pm2 list
   ```

3. **Save the PM2 Process List**

   To ensure the app restarts after reboot:

   ```bash
   pm2 save
   ```

## Step 6: Set Up PM2 to Auto-Start on Reboot

To ensure PM2 restarts your application after a server reboot, configure PM2 as a startup service.

1. **Generate the Startup Script**

   ```bash
   pm2 startup
   ```

2. **Follow the Instructions**

   The command above will display a command to execute. Follow the instructions and run that command.

3. **Save the PM2 Process List Again**

   ```bash
   pm2 save
   ```

## Step 7: Configure DNS for `yourdomain.in` Domain

To point your domain **yourdomain.in** to your server, update the DNS settings of your domain.

1. **Login to your Domain Registrar’s Dashboard**

   - Go to the DNS management page for **yourdomain.in** (this might be through your domain registrar like GoDaddy, Namecheap, etc.).

2. **Add an A Record**

   - Set up an A record to point your domain to your server’s public IP address.

     Example:
     - **Host**: `@`
     - **Type**: `A`
     - **Value**: Your server’s IP (e.g., `192.168.1.1`).
     - **TTL**: `1 hour` (or leave default).

3. **DNS Propagation**

   It may take a few minutes to hours for the DNS changes to propagate.

## Step 8: Set Up a Reverse Proxy with Nginx

1. **Install Nginx**

   ```bash
   sudo apt install nginx
   ```

2. **Create a New Nginx Configuration for Your Node.js App**

   Create a new configuration file for **yourdomain.in**:

   ```bash
   sudo nano /etc/nginx/sites-available/yourdomain.in
   ```

   Add the following configuration, replacing `your_project_port` with the actual port your app is running on (e.g., `3000`):

   ```nginx
   server {
       listen 80;
       server_name yourdomain.in www.yourdomain.in;

       location / {
           proxy_pass http://localhost:your_project_port;
           proxy_http_version 1.1;
           proxy_set_header Upgrade $http_upgrade;
           proxy_set_header Connection 'upgrade';
           proxy_set_header Host $host;
           proxy_cache_bypass $http_upgrade;
       }
   }
   ```

3. **Enable the Nginx Configuration**

   Create a symbolic link to enable the configuration:

   ```bash
   sudo ln -s /etc/nginx/sites-available/yourdomain.in /etc/nginx/sites-enabled/
   ```

4. **Test the Nginx Configuration**

   Ensure there are no syntax errors:

   ```bash
   sudo nginx -t
   ```

5. **Restart Nginx**

   Restart Nginx to apply the changes:

   ```bash
   sudo systemctl restart nginx
   ```

6. **Allow HTTP Traffic Through the Firewall**

   If you're using `ufw`, allow HTTP traffic:

   ```bash
   sudo ufw allow 'Nginx Full'
   ```

## Step 9: Enable SSL with Let's Encrypt

To secure your website with HTTPS, you can use **Let’s Encrypt** SSL certificates.

1. **Install Certbot and Nginx Plugin**

   ```bash
   sudo apt install certbot python3-certbot-nginx
   ```

2. **Obtain the SSL Certificate**

   Run the following command to obtain and install the SSL certificate for **yourdomain.in**:

   ```bash
   sudo certbot --nginx -d yourdomain.in -d www.yourdomain.in
   ```

   Certbot will automatically obtain the SSL certificate and configure Nginx for HTTPS.

3. **Confirm SSL Installation**

   Once the process is complete, Certbot will give you a success message. You can verify the SSL by visiting `https://yourdomain.in` in your browser.

4. **Automatic Certificate Renewal**

   Certbot will set up a cron job for automatic certificate renewal. You can test the renewal process by running:

   ```bash
   sudo certbot renew --dry-run
   ```

## Step 10: Access the Application

Now, your Node.js application should be accessible via **yourdomain.in** with HTTPS.

1. **Visit the Domain**

   Open your browser and go to `https://yourdomain.in`. You should see your Node.js app running securely over HTTPS.

## Step 11: Monitoring the Application

To monitor the logs of your Node.js application:

```bash
pm2 logs
```

---

## Conclusion

With these steps, you've successfully:

1. Logged into your server using SSH.
2. Cloned your Node.js project from GitHub.
3. Set up PM2 to manage the application with a custom process name (`your-app-name`).
4. Configured **yourdomain.in** domain to point to your server.
5. Set up a reverse proxy with Nginx.
6. Enabled SSL with Let’s Encrypt to serve your app over HTTPS.

To update the project in the future, you can simply pull the latest changes from GitHub:

```bash
git pull origin main
pm2 restart your-app-name
```

--- 

This is the complete README file for setting up your Node.js app on an Ubuntu server with PM2, a custom project name, domain setup for **yourdomain.in**, and SSL.
