# wordpress-docker-compose-with-ssl

This repository provides a simple and efficient way to set up WordPress with SSL (HTTPS) using Docker Compose and Let's Encrypt

**Prerequisites:**
*   Docker and Docker Compose (2.x) installed on your server.
*   A domain name (e.g., `yourdomain.com`) with correctly configured DNS records pointing to your server's IP address.  **This is crucial; if your domain doesn't resolve, the SSL certificate generation will fail and rest of the setup will fail**



**Installation:**

1.  **Create Directory Structure:**

    ```bash
    mkdir -p /opt/wordpress
    cd /opt/wordpress
    mkdir config
    mkdir -p nginx/
    ```

2.  **`docker-compose.yml`:**

    Create a `docker-compose.yml` file in the `/opt/wordpress` directory.  **Important:** Replace `yourdomain.com` and `www.yourdomain.com` with your actual domain(s) and update the email address.
    
3.  ** The .env File **

    You can create a `.env` file in the same directory as `docker-compose.yml` to store environment variables.  This is a good practice for security and organization.


4.  **Run Docker Compose:**
    ```bash
    docker compose up -d
    ```

5.  **WordPress Installation:**

    Wait a few minutes for the containers to start and the SSL certificate to be generated. Then, visit `https://yourdomain.com` in your browser to complete the WordPress installation.

