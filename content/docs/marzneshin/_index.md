---
title: Basic install Marzneshin 
linkTitle : Marzneshin
toc: False
weight: 1
---

To get started, you need a Linux machine.

{{< callout type="info" >}}
We recommend Ubuntu for its ease of use, though Marzneshin can run on any Linux distribution.
{{< /callout >}}

Marzneshin supports both ARM and x86 architectures. Docker is also supported.

{{< callout type="info" >}}
Quick installation:

```bash
sudo bash -c "$(curl -sL https://github.com/marzneshin/Marzneshin/raw/master/script.sh)" @ install
```

After that, create an admin:

```bash
marzneshin cli admin create --sudo
```

{{< /callout >}}

Marzneshin supports the following databases. SQLite is preferred for small setups, while MariaDB is recommended for larger configurations.
{{< tabs items="mariadb,mysql,sqlite" >}}

{{< tab >}}```bash
sudo bash -c "$(curl -sL https://github.com/marzneshin/Marzneshin/raw/master/script.sh)" @ install --database mariadb
```{{< /tab >}}
{{< tab >}}```bash
sudo bash -c "$(curl -sL https://github.com/marzneshin/Marzneshin/raw/master/script.sh)" @ install --database mysql
```{{< /tab >}}
{{< tab >}}```bash
sudo bash -c "$(curl -sL https://github.com/marzneshin/Marzneshin/raw/master/script.sh)" @ install
```{{< /tab >}}

{{< /tabs >}}

{{< callout type="warning" >}}
To install the latest **nightly** release, use the `--nightly` flag.
{{< /callout >}}

Once the installation is complete:

- You'd notice the logs, which you can stop watching by pressing `Ctrl+C`. The process will continue running normally.
- The configuration file can be found at `/etc/opt/marzneshin/.env` (refer to the [configuration](/docs/configuration/marzneshin) page).
- Data files will be placed at `/var/lib/marzneshin`, e.g., the SQLite database.
- You can access the Marzneshin dashboard by opening a web browser and navigating to `http://<SERVER_IP>:8000/dashboard/`.

Next, create a sudo admin for logging into the Marzneshin dashboard using the following command:

```bash
marzneshin cli admin create --sudo
```

That's it! You can log in to your dashboard using these credentials.

To see the help message of the Marzneshin script, run the following command:

```bash
marzneshin --help
```
