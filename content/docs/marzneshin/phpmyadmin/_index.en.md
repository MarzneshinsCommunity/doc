---
title: phpmyadmin  
weight: 6  
---

`phpMyAdmin` is a powerful and user-friendly tool for managing MySQL/MariaDB databases through a web-based interface. It allows you to execute queries, manage tables, and configure database settings with ease. Follow the steps below to set up `phpMyAdmin` in Marzneshin.

{{% steps %}}

### Edit the Docker Compose File

```bash
nano /etc/opt/marzneshin/docker-compose.yml
```

### Add the phpMyAdmin Service

Please note:  
- **Indentation** in YAML files is crucial.  
- You can **adjust ports** as needed.  

```yaml
  phpmyadmin:
    image: phpmyadmin/phpmyadmin:latest
    restart: always
    env_file: .env
    network_mode: host
    environment:
      PMA_HOST: 127.0.0.1
      PMA_PORT: 3306
      APACHE_PORT: 8010
      UPLOAD_LIMIT: 1024M
    depends_on:
      - db
```

### Restart the Marzneshin Service

```bash
marzneshin restart
```

Now `phpMyAdmin` is ready, and you can access it by navigating to `http://IP:PORT` in your browser. Use the `root` username and your database password to log in.

{{< callout type="warning" >}}

⚠️ **Warning:**  
Please avoid making changes to your database directly. Always take a backup before applying any modifications.

{{< /callout >}}

{{% /steps %}}