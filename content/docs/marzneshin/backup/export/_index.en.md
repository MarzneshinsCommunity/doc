---
title: Data Export
weight: 1
---

{{< tabs items="SQLite, MariaDB, MySQL" >}}

{{< tab >}}  

### Backup Files

Your Marzneshin data is stored in the following directories:

- `/etc/opt/marzneshin/`
- `/var/lib/marzneshin/`
- `/var/lib/marznode/`

{{< /tab >}}  

{{< tab >}}  

{{% steps %}}

### Backup Files
Your Marzneshin data is stored in the following directories:

- `/etc/opt/marzneshin/`
- `/var/lib/marzneshin/`
- `/var/lib/marznode/`

{{< callout type="warning" >}}
**Important:** The directory `/var/lib/marzneshin/mysql` should not be backed up. If you have mistakenly backed it up, make sure to delete it before proceeding.
{{< /callout >}}

### Install Required Tools
To ensure the necessary tools are installed, run the following command:

```bash
docker exec -it marzneshin-db-1 bash -c "apt update && apt install -y mariadb-client"
```

### Set Database Password
Define your database password using the following command:

```bash
export MARZDBPASS="pass"
```

### Backup Database
Run the following command to create a backup of your database:

```bash
docker exec -i marzneshin-db-1 mariadb-dump -u root -p$MARZDBPASS marzneshin > /var/lib/marzneshin/marzneshin-$(date +%F).sql
```

{{% /steps %}}

The backup file will be saved in `/var/lib/marzneshin` with the current date.

{{< /tab >}}  

{{< tab >}}  

{{% steps %}}

### Backup Files
Your Marzneshin data is stored in the following directories:

- `/etc/opt/marzneshin/`
- `/var/lib/marzneshin/`
- `/var/lib/marznode/`

{{< callout type="warning" >}}
**Important:** The directory `/var/lib/marzneshin/mysql` should not be backed up. If you have mistakenly backed it up, make sure to delete it before proceeding.
{{< /callout >}}

### Install Required Tools
To ensure the necessary tools are installed, run the following command:

```bash
docker exec -it marzneshin-db-1 bash -c "apt update && apt install -y mysql-client"
```

### Set Database Password
Define your database password using the following command:

```bash
export MARZDBPASS="pass"
```

### Backup Database
Run the following command to create a backup of your database:

```bash
docker exec -i marzneshin-db-1 mysqldump -u root -p$MARZDBPASS marzneshin > /var/lib/marzneshin/marzneshin-$(date +%F).sql
```

{{% /steps %}}

The backup file will be saved in `/var/lib/marzneshin` with the current date.

{{< /tab >}}  

{{< /tabs >}}
