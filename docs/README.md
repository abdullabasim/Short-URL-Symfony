# Short URL

A highly secure and user-friendly self-hosted URL shortener service that provides simplicity and privacy.

##  Installation

Create a `docker-compose.yml` file in an empty directory.

```yaml
version: '3.6'

services:
  app:
    image: ghcr.io/nicklog/shorti
    environment:
      - TZ=Asia/Baghdad
      - DATABASE_NAME=short_url
      - DATABASE_USER=short_url
      - DATABASE_PASSWORD=password
      - DATABASE_HOST=database
      - DATABASE_PORT=3306
    depends_on:
      - database
    networks:
      - default

  database:
    image: mariadb:latest
    environment:
      - MYSQL_DATABASE=short_url
      - MYSQL_USER=short_url
      - MYSQL_PASSWORD=password
      - MYSQL_ROOT_PASSWORD=password
    networks:
      - default
```

Customize the settings according to your requirements and effortlessly deploy the application using the command `docker-compose up -d`. Once deployed, you can access the website on port 80.

Please note that in this example setup, the website is not secured with HTTPS. To ensure secure access, I recommend utilizing a reverse proxy. By implementing a reverse proxy, you can add an additional layer of security and enable HTTPS encryption for enhanced protection of your website and user data.

## User

On the initial visit to the website, you have the ability to create a user account. Once created, you can log in using your credentials. As the first user, you will automatically be granted admin privileges, allowing you to manage and create additional user accounts as needed. This ensures a seamless and scalable user management system within the website.

##  Update

Just update the docker image with...
```bash
docker-compose pull
docker-compose up -d
```
