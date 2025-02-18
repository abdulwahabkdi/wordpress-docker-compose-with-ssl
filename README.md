# wordpress-docker-compose-with-ssl

This repository provides a simple and efficient way to set up WordPress with SSL (HTTPS) using Docker Compose and Let's Encrypt

**Prerequisites:**
*   Docker and Docker Compose (2.x) installed on your server.
*   A domain name (e.g., `yourdomain.com`) with correctly configured DNS records pointing to your server's IP address.  **This is crucial; if your domain doesn't resolve, the SSL certificate generation will fail and rest of the setup will fail**



**Installation:**

1. **Install Docker and Docker compose**

   Ubuntu
  ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  sudo apt update && sudo apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
```

RHEL 8/9
 ```bash
 sudo dnf -y install dnf-plugins-core
 sudo dnf config-manager --add-repo https://download.docker.com/linux/rhel/docker-ce.repo
 sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
 ```
2.  **Create Directory Structure:**

    ```bash
    mkdir -p /opt/wordpress
    cd /opt/wordpress
    mkdir config
    mkdir -p nginx/
    ```

3.  **`docker-compose.yml`:**

    Create a `docker-compose.yml` file in the `/opt/wordpress` directory.  **Important:** Replace `yourdomain.com` and `www.yourdomain.com` with your actual domain(s) and update the email address.
    
4.  ** The .env File **

    You can create a `.env` file in the same directory as `docker-compose.yml` to store environment variables.  This is a good practice for security and organization.


5.  **Run Docker Compose:**
    ```bash
    docker compose up -d
    ```

6.  **WordPress Installation:**

    Wait a few minutes for the containers to start and the SSL certificate to be generated. Then, visit `https://yourdomain.com` in your browser to complete the WordPress installation.

