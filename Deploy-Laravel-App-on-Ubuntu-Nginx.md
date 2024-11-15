# Hosting a Laravel Project on Ubuntu Server with Nginx, SSL, and `yourdomain.in` Domain

This guide explains how to set up a Laravel project on an Ubuntu server with **Nginx** as the web server, **Let's Encrypt SSL** for secure connections, and configuring the **yourdomain.in** domain to point to your application.

## Prerequisites

- A blank Ubuntu server (Ubuntu 20.04 or later).
- SSH access to the server.
- A GitHub repository containing your Laravel project.
- A domain name **yourdomain.in** pointing to your server’s IP address.
- Basic knowledge of the command line and server management.

## Step 0: SSH Login to the Server

Log in to your Ubuntu server via SSH using the following command. Replace `your-server-ip` with the IP address of your server and `your-username` with your username (e.g., `ubuntu` or `root`):

```bash
ssh your-username@your-server-ip
```

For example:

```bash
ssh ubuntu@192.168.1.1
```

If you're using an SSH key for authentication, specify the private key file with the `-i` option:

```bash
ssh -i /path/to/your/private-key.pem your-username@your-server-ip
```

## Step 1: Update and Upgrade the System

Before starting, make sure the server is up-to-date.

```bash
sudo apt update && sudo apt upgrade -y
```

## Step 2: Install Nginx and PHP

Laravel requires PHP and Nginx. Follow these steps to install them:

1. **Install Nginx**

   ```bash
   sudo apt install nginx
   ```

2. **Install PHP and Required Extensions**

   Laravel requires PHP 8.1 or higher. Run the following commands to install PHP and the necessary extensions:

   ```bash
   sudo apt install php-fpm php-cli php-mbstring php-xml php-curl php-mysql php-zip php-bcmath php-json
   ```

3. **Verify PHP Installation**

   Check the installed version of PHP:

   ```bash
   php -v
   ```

## Step 3: Install Git

If Git is not installed, run the following command to install it:

```bash
sudo apt install git
```

## Step 4: Clone Your Laravel Project from GitHub

1. **Clone the GitHub Repository**

   Replace `your-repository-url` with the URL of your GitHub repository (e.g., `https://github.com/username/your-laravel-project.git`).

   ```bash
   git clone https://github.com/username/your-laravel-project.git
   ```

2. **Navigate to Your Project Directory**

   ```bash
   cd your-laravel-project
   ```

## Step 5: Configure the `.env` File

1. **Create the `.env` File**

   If the `.env` file doesn't exist, create one by copying the `.env.example` file:

   ```bash
   cp .env.example .env
   ```

2. **Edit the `.env` File**

   Use a text editor to configure the `.env` file with your database and other necessary configurations:

   ```bash
   nano .env
   ```

   Update the following values (example):

   - `DB_CONNECTION=mysql`
   - `DB_HOST=127.0.0.1`
   - `DB_PORT=3306`
   - `DB_DATABASE=your_database`
   - `DB_USERNAME=your_db_user`
   - `DB_PASSWORD=your_db_password`

   Save the file after making changes (`Ctrl+X` to exit and `Y` to confirm).

## Step 6: Install Composer

Laravel uses Composer for dependency management. Install Composer globally on your server:

1. **Download Composer**

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

2. **Move Composer to Global Directory**

   ```bash
   sudo mv composer.phar /usr/local/bin/composer
   ```

3. **Verify Composer Installation**

   ```bash
   composer --version
   ```

## Step 7: Install Laravel Dependencies

Now, install the necessary Laravel dependencies using Composer:

```bash
composer install
```

## Step 8: Set Permissions for Laravel

Ensure that the appropriate permissions are set for the Laravel project:

1. **Set Permissions on Storage and Bootstrap Directories**

   ```bash
   sudo chown -R www-data:www-data /path/to/your-laravel-project/storage
   sudo chown -R www-data:www-data /path/to/your-laravel-project/bootstrap/cache
   ```

2. **Make Directories Writable**

   ```bash
   sudo chmod -R 775 /path/to/your-laravel-project/storage
   sudo chmod -R 775 /path/to/your-laravel-project/bootstrap/cache
   ```

## Step 9: Run Migrations and Seed Database

1. **Run Migrations**

   To apply database migrations, run:

   ```bash
   php artisan migrate
   ```

2. **Run Database Seeders (Optional)**

   If you have seeders set up, run the following command to populate your database:

   ```bash
   php artisan db:seed
   ```

## Step 10: Configure Nginx as a Web Server

1. **Create a New Nginx Configuration File**

   Create a new Nginx configuration file for **yourdomain.in**:

   ```bash
   sudo nano /etc/nginx/sites-available/yourdomain.in
   ```

   Add the following configuration:

   ```nginx
   server {
       listen 80;
       server_name yourdomain.in www.yourdomain.in;

       root /path/to/your-laravel-project/public;
       index index.php index.html index.htm;

       location / {
           try_files $uri $uri/ /index.php?$query_string;
       }

       location ~ \.php$ {
           include snippets/fastcgi-php.conf;
           fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;
           fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
           include fastcgi_params;
       }

       location ~ /\.ht {
           deny all;
       }

       error_log  /var/log/nginx/yourdomain.in_error.log;
       access_log /var/log/nginx/yourdomain.in_access.log;
   }
   ```

2. **Enable the Site and Restart Nginx**

   Enable the site configuration:

   ```bash
   sudo ln -s /etc/nginx/sites-available/yourdomain.in /etc/nginx/sites-enabled/
   ```

   Test the Nginx configuration:

   ```bash
   sudo nginx -t
   ```

   If the test is successful, restart Nginx:

   ```bash
   sudo systemctl restart nginx
   ```

3. **Allow HTTP Traffic Through the Firewall**

   If you're using `ufw`, allow HTTP and HTTPS traffic:

   ```bash
   sudo ufw allow 'Nginx Full'
   ```

## Step 11: Set Up SSL with Let's Encrypt

1. **Install Certbot and Nginx Plugin**

   ```bash
   sudo apt install certbot python3-certbot-nginx
   ```

2. **Obtain SSL Certificate**

   Run the following command to obtain and install the SSL certificate for **yourdomain.in**:

   ```bash
   sudo certbot --nginx -d yourdomain.in -d www.yourdomain.in
   ```

3. **Verify SSL Installation**

   Certbot will automatically configure SSL. Verify by visiting `https://yourdomain.in`.

4. **Automatic SSL Certificate Renewal**

   Certbot will handle automatic renewals. You can test the renewal process with:

   ```bash
   sudo certbot renew --dry-run
   ```

## Step 12: Access the Application

Visit `https://yourdomain.in` in your browser to access your Laravel application securely over HTTPS.

---

## Conclusion

With these steps, you have:

1. Set up Nginx to serve your Laravel application.
2. Configured your `.env` file for database and environment settings.
3. Applied Laravel migrations and database seeders.
4. Configured SSL using Let's Encrypt.

---

## Thank You!

Thank you for following this guide! We hope it was helpful in setting up your Laravel application on your Ubuntu server using Nginx. If you have any further questions or run into any issues, feel free to reach out.

Happy coding! 😊
