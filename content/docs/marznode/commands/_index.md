---
title: Commands  
weight: 5  
---

First, navigate to the `marznode` directory:

```bash
cd /var/lib/marznode
```

### Start

To start Docker and run the services in the background, use the following command:

```bash
docker-compose up -d
```

### Stop

To stop the running services, use the following command:

```bash
docker-compose down
```

### Restart

To restart the services, use the following command:

```bash
docker-compose restart
```

### Update

To update the containers and restart the services, first stop the containers, then download and install the updates:

```bash
docker-compose down && docker-compose pull && docker-compose up -d
```

### Logs

To view the logs of the Docker containers, use the following command:

```bash
docker-compose logs
```

### Status

To check the current status of the services and containers, use the following command:

```bash
docker-compose ps
```
