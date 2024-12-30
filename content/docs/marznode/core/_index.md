---
title: Cores
weight: 3
---
{{< callout emoji="🌐" >}}
This page explains how to configure and set up the following cores.
{{< /callout >}}


As explained, MarzNode uses the following three cores as its central cores.
Click on each tab to view the corresponding details.


{{< tabs items="Xray,hysteria2,SingBox" >}}

{{< tab >}}
{{< callout type="info" >}}
When MarzNode is installed, the Xray core is activated by default. No additional configuration is required for this core.
{{< /callout >}}


To disable the Xray core, set the following variable:


  `XRAY_ENABLED:` `"False"` / `"True"`
 
```bash
  XRAY_ENABLED: "False"
 ```
 {{< /tab >}}

 {{< tab >}}
 {{< callout type="info" >}}
  Follow the certificate generation guide for MarzNode to generate a certificate for your node and add it to the Hysteria inbound configuration to activate the Hysteria core.
 {{< /callout >}}

{{% steps %}}

### Download the Hysteria2 Config File:
*  Use the following command to download the config file and save it to the specified path:
    - ```bash
       curl -L https://github.com/marzneshin/marznode/raw/master/hysteria.yaml > /var/lib/marznode/hysteria.yaml
       ```
### Edit the MarzNode Configuration File:
* Navigate to the MarzNode directory and open the Docker Compose configuration file:
    - ```bash
       cd marznode && nano compose.yml
      ```
##### Edit the Local Node Configuration File:
* For the local node, edit the following file:
    - ```bash
      nano /etc/opt/marzneshin/docker-compose.yml
      ```

### Add the Following Variables to the Docker Configuration File:

  ```bash
HYSTERIA_CONFIG_PATH: "/var/lib/marznode/hysteria.yaml"  
HYSTERIA_ENABLED: "True"  
 ```

### Restart MarzNode:
* After making the changes, restart the MarzNode service using:

    - ```bash
      docker compose down && docker compose up -d
      ```
##### Restart the Local Node:
* For the local node, use the following command:
    
     - ```bash
       marzneshin restart
        ```


> #### To disable the Hysteria core, set the following variable:
> 
> * `HYSTERIA_ENABLED:` `"False"` / `True`
>    - ```bash
>       HYSTERIA_ENABLED: "False"  
>      ```
>
   {{% /steps %}}

  {{< /tab >}}
  {{< tab >}}
 {{% steps %}}

 ### Download the Sing-Box Config File:
  * Use the following command to download the config file and save it to the specified path:

     - ```bash
         curl -L https://raw.githubusercontent.com/MarzneshinsCommunity/files/refs/heads/main/sing-box.json > /var/lib/marznode/sing-box.json
         ```

### Edit the MarzNode Configuration File:
* Navigate to the MarzNode directory and open the Docker Compose configuration file:
    - ```bash
       cd marznode && nano compose.yml
        ```
##### Edit the Local Node Configuration File:
*  For the local node, edit the following file:
    - ```bash
       nano /etc/opt/marzneshin/docker-compose.yml
        ```

### Add the Following Variables to the Docker Configuration File:
* ```bash
  SING_BOX_ENABLED: "True"
  SING_BOX_CONFIG_PATH: "/var/lib/marznode/sing-box.json"

   ```
### Restart MarzNode:
* After making the changes, restart the MarzNode service using:
    - ```bash
       docker compose down && docker compose up -d
        ```
##### Restart the Local Node:
* For the local node, use the following command:
    - ```bash 
       marzneshin restart
       ```
 >   #### To disable the SingBox core, set the following variable:
 >  * `SING_BOX_ENABLED:` `"False"` / `"True"`
 >       - ```bash
 >           SING_BOX_ENABLED: "False"
 >           ```

  {{% /steps %}}
  {{< /tab >}}

  {{< /tabs >}}
