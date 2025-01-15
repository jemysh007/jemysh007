## **Complete Deployment Documentation NodeJS using Docker**

### **Overview**

This guide walks you through deploying the `demo` Node.js application in a **Dockerized environment** with **Nginx** as a reverse proxy, **Let's Encrypt** for automatic SSL management, and using **GitHub** for the application source.

The application will be available on **demo.jemish.in** with automatic SSL (HTTPS) via Let's Encrypt.

### **Prerequisites**

1. **Docker** and **Docker Compose** installed on the server.
   - Install Docker: [Docker installation guide](https://docs.docker.com/get-docker/)
   - Install Docker Compose: [Docker Compose installation guide](https://docs.docker.com/compose/install/)
2. A domain (`demo.jemish.in`) pointing to your server's IP address.
3. Open ports **80** (HTTP) and **443** (HTTPS).
4. Git installed on the server.
5. Your **GitHub repository** for the application at `https://github.com/jemysh007/demo`.

---

### **Step 1: Clone the Repository**

SSH into your server and clone the GitHub repository:

```bash
git clone https://github.com/jemysh007/demo.git
cd demo
```

---

### **Step 2: Directory Structure**

Ensure your project follows the structure below, and place the `Dockerfile` in the `app/` folder:

```plaintext
demo/
├── app/                 # Node.js application
│   ├── server.js        # Main server file
│   ├── package.json     # Dependencies
│   ├── .env             # Environment variables
│   ├── Dockerfile       # Dockerfile for Node.js app
│   ├── .dockerignore    # Ignore unnecessary files in Docker
├── nginx/               # Nginx configuration
│   ├── nginx.conf       # Reverse proxy config
│   └── ssl/             # SSL certificates
├── docker-compose.yml   # Docker Compose file
└── deploy.sh            # Deployment script
```

---

### **Step 3: Prepare the Node.js App**

#### **Environment Variables**

Create a `.env` file inside the `app/` directory:

```plaintext
PORT=3000
NODE_ENV=production
```

#### **Node.js `Dockerfile`**

**`app/Dockerfile`:**

```dockerfile
# Use Node.js official image
FROM node:18-slim

# Set working directory
WORKDIR /usr/src/app

# Copy package files and install dependencies
COPY package*.json ./
RUN npm install --production

# Copy the application code
COPY . .

# Expose port
EXPOSE 3000

# Command to start the app
CMD ["npm", "start"]
```

#### **Docker Ignore File**

**`app/.dockerignore`:**

```plaintext
node_modules
npm-debug.log
.env
.git
```

---

### **Step 4: Configure Nginx**

#### **Nginx Configuration**

Nginx will handle SSL termination and reverse proxying traffic to the Node.js app. It will forward the HTTP traffic to the app over the internal network.

**`nginx/nginx.conf`:**

```nginx
server {
    server_name demo.jemish.in;

    # Redirect HTTP to HTTPS
    listen 80;
    return 301 https://$host$request_uri;

    # HTTPS Configuration
    listen 443 ssl;
    ssl_certificate /etc/letsencrypt/live/demo.jemish.in/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/demo.jemish.in/privkey.pem;

    location / {
        proxy_pass http://app:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

---

### **Step 5: Create Docker Compose File**

**`docker-compose.yml`:**

```yaml
version: "3.8"

services:
  app:
    build:
      context: ./app # Path to the folder containing the Dockerfile
    ports:
      - "3000:3000"
    env_file:
      - ./app/.env
    container_name: demo-app
    restart: always

  nginx:
    image: nginx:latest
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - ./nginx/nginx.conf:/etc/nginx/nginx.conf
      - /etc/letsencrypt:/etc/letsencrypt
    depends_on:
      - app
    container_name: demo-nginx

  certbot:
    image: certbot/certbot
    volumes:
      - /etc/letsencrypt:/etc/letsencrypt
      - /var/lib/letsencrypt:/var/lib/letsencrypt
    entrypoint: /bin/sh -c "trap exit TERM; while :; do sleep 12h & wait $${!}; certbot renew; done;"
```

---

### **Step 6: Create Deployment Script**

Create a `deploy.sh` script to automate pulling the latest changes from GitHub and redeploying the app.

**`deploy.sh`:**

```bash
#!/bin/bash

echo "Pulling latest changes from GitHub..."
git pull origin main

echo "Rebuilding Docker containers..."
docker-compose build app

echo "Restarting services..."
docker-compose up -d

echo "Deployment complete!"
```

Make it executable:

```bash
chmod +x deploy.sh
```

---

### **Step 7: Generate SSL Certificates**

Run Certbot to generate SSL certificates using Let's Encrypt.

1. First, run the `certbot` container to request SSL certificates:

   ```bash
   docker run --rm -v /etc/letsencrypt:/etc/letsencrypt -v /var/lib/letsencrypt:/var/lib/letsencrypt certbot/certbot certonly \
     --standalone -d demo.jemish.in --email your-email@example.com --agree-tos --non-interactive
   ```

2. Verify that the certificates were generated:
   ```bash
   ls /etc/letsencrypt/live/demo.jemish.in
   ```

---

### **Step 8: Build and Run the Containers**

1. Build the Docker images:

   ```bash
   docker-compose build
   ```

2. Start the services:

   ```bash
   docker-compose up -d
   ```

3. Ensure the application is running:
   - HTTP traffic should be redirected to HTTPS by Nginx.
   - Your Node.js app is running behind Nginx, and Nginx is handling SSL.

---

### **Step 9: Logs and Monitoring**

#### **View Logs**

- **App Logs**:
  ```bash
  docker logs demo-app
  ```
- **Nginx Logs**:
  ```bash
  docker logs demo-nginx
  ```

#### **Continuous Monitoring**

You can use Docker monitoring tools like **Portainer** or **Docker Dashboard** to manage and monitor your containers.

---

### **Step 10: Automate SSL Certificate Renewal**

Certbot will automatically renew your SSL certificates. The `certbot` container is set up to run a cron job inside the container to check for renewal every 12 hours.

---

### **Step 11: Automate with GitHub Actions (Optional)**

To automate the deployment process with GitHub Actions:

1. Set up a `.github/workflows/deploy.yml` file in your repository.
2. Configure the GitHub Actions workflow to pull the latest code and run the `deploy.sh` script.

---

### **Summary**

- **Domain**: `demo.jemish.in`
- **Components**:
  - Node.js app container (`demo-app`).
  - Nginx reverse proxy (`demo-nginx`).
  - Certbot for SSL automation (`certbot`).
- **Git Integration**: Pull the latest code via `deploy.sh`.
- **Logs**: Access via `docker logs`.
