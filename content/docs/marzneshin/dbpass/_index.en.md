---
title: Database Password
toc: false  
weight: 2  
---

The default password for MariaDB and MySQL databases in Marzneshin is `12341234`. After taking a backup, follow the steps below to change the password.

{{% steps %}}

### 1. Log in to the Database

To apply changes, you must first log in to the database. Use the appropriate command for your database:

{{< tabs items="mariadb,mysql" >}}

{{< tab >}}  
```bash  
docker exec -it marzneshin-db-1 mariadb -u root -p
```  
{{< /tab >}}  

{{< tab >}}  
```bash  
docker exec -it marzneshin-db-1 mysql -u root -p
```  
{{< /tab >}}  

{{< /tabs >}}

### 2. Change the Database Password

To change the password, run the following command:

```sql
ALTER USER 'root'@'%' IDENTIFIED BY 'NEW PASSWORD';
FLUSH PRIVILEGES;
```

### 3. Exit the Database

To exit the database, run the following command twice:

```bash
exit
```

### 4. Edit the Docker File

To change the password in the Docker file, run the following command:

```bash
nano /etc/opt/marzneshin/docker-compose.yml
```

Then, edit the following values:

{{< tabs items="mariadb,mysql" >}}

{{< tab >}}  

```yaml
SQLALCHEMY_DATABASE_URL: "mariadb+pymysql://root:NEWPASSWORD@127.0.0.1/marzneshin"
MARIADB_ROOT_PASSWORD: "NEW PASSWORD" 
```  

{{< /tab >}}  

{{< tab >}}  

```yaml
SQLALCHEMY_DATABASE_URL: "mysql+pymysql://root:NEWPASSWORD@127.0.0.1/marzneshin"
MYSQL_ROOT_PASSWORD: "NEW PASSWORD" 
```  

{{< /tab >}}  

{{< /tabs >}}

### 5. Restart Marzneshin

To apply the changes, restart Marzneshin using the following command:

```bash
marzneshin restart
```

Once you complete these steps, your database password will be changed.

{{% /steps %}}
