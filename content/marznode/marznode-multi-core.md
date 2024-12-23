---
title: "Activating MarzNode Cores"
---

   
 ___
  
### This guide explains the configuration and setup process for the following cores:

{{% steps %}}

### **Xray**  
### **hysteria2**
### **SingBox**  
### **Additional Details**

{{% /steps %}}
 ___


{{% steps %}}

### Xray Core :
* When MarzNode is installed, the Xray core is activated by default. No additional configuration is required for this core.

>#### To disable the Xray core, set the following variable:
>* `XRAY_ENABLED:` `"False"` / `"True"`
>    - ```bash
>        XRAY_ENABLED: "False"
>       ```
>
>
  
__The End ___

### Hysteria2 Core :

{{< callout type="info" >}}

Follow the [certificate generation guide for MarzNode](nskskks) to generate a certificate for your node and add it to the Hysteria inbound configuration to activate the Hysteria core.

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
### Edit the Local Node Configuration File:
* For the local node, edit the following file:
    - ```bash
      nano /etc/opt/marzneshin/docker-compose.yml
      ```

### Add the Following Variables to the Docker Configuration File:

  ```bash
HYSTERIA_CONFIG_PATH: "/var/lib/>marznode/hysteria.yaml"  
HYSTERIA_ENABLED: "True"  
 ```

### Restart MarzNode:
* After making the changes, restart the MarzNode service using:

    - ```bash
      docker compose down && docker compose up -d
      ```
### Restart the Local Node:
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

___The End ___


### Sing-Box core :
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
### Edit the Local Node Configuration File:
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
### Restart the Local Node:
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

  ___ The End ___

  ### Additional Details:
{{% /steps %}}

{{% details title="Additional Details"closed="true" %}}

## General Variables and Their Usage

{{% steps %}}

### True and False  
In configuration variables, the values `True` and `False` are used to control the status of features and services:  
* **True**: Used to enable a feature or service.  
* **False**: Used to disable a feature or service.  
- To enable a feature, set the variable to `True`.  
- To disable a feature, set the variable to `False`.  

___  

### DEBUG  
* This variable is used to toggle the debug mode.  
  - ```bash
      DEBUG: "True"
      ```  
* **True**: Enables debug mode, providing more detailed logs to troubleshoot issues.  
* **False**: Disables debug mode, showing only essential information.  

___  

### AUTH_GENERATION_ALGORITHM  

* This variable specifies the algorithm used for generating hashes or authentication keys.  

    - ```bash
      AUTH_GENERATION_ALGORITHM: "xxh128"
       ```  
* **xxh128**: A 128-bit version of the xxHash algorithm, known for its high speed and suitability for scenarios requiring fast hash generation with low collision probability.  
* **sha256**: A secure and standard algorithm, ideal for sensitive security applications.  
* **md5**: An older algorithm with high speed but low security, recommended only for non-critical use cases.  

> **xxh128**: Ideal for environments where speed and performance are critical.  
> **sha256**: Recommended for applications prioritizing security over speed.  
> **md5**: Only use for non-sensitive applications.  

___  

### Managing the `XRAY` Service in Marzneshin  

#### Variables and Descriptions:  

> A variable to enable or disable the XRAY service.  
> * `XRAY_ENABLED:` `"True" / "False"`  

> Path to the XRAY executable used to launch the service.  
> * `XRAY_EXECUTABLE_PATH:` `"/usr/local/bin/xray"`  

> Path to XRAY’s asset files and libraries.  
> * `XRAY_ASSETS_PATH:` `"/usr/local/lib/xray"`  

> A variable for enabling or modifying the Flow in VLESS configuration with Reality support.  
> * `XRAY_VLESS_REALITY_FLOW:` `"xtls-rprx-vision"`  

> Specifies whether XRAY should automatically restart in case of failure.  
> * `XRAY_RESTART_ON_FAILURE:` `"True" / "False"`  

> The interval (in seconds) between automatic restart attempts after XRAY encounters an error.  
> * `XRAY_RESTART_ON_FAILURE_INTERVAL: "0"`  
>
> **Usage**: If restart attempts are needed, set a specific interval in seconds.  

___  

### Managing the Hysteria Service in Marzneshin  

#### Variables and Descriptions:  

> A variable to enable or disable the Hysteria service.  
> * `HYSTERIA_ENABLED:` `"True" / "False"`  

> Path to the Hysteria executable used to launch the service.  
> * `HYSTERIA_EXECUTABLE_PATH:` `"/usr/bin/hysteria"`  

> Path to Hysteria’s configuration file containing the key service settings.  
> * `HYSTERIA_CONFIG_PATH:` `"/var/lib/marznode/hysteria.yaml"`  

___  

### Managing the Sing-Box Service in Marzneshin  

#### Variables and Descriptions:  

> A variable to enable or disable the Sing-Box service.  
> * `SING_BOX_ENABLED:` `"True" / "False"`  

> Path to the Sing-Box executable used to run the service.  
> * `SING_BOX_EXECUTABLE_PATH:` `"/usr/bin/sing-box"`  

> Path to Sing-Box’s configuration file containing key service settings.  
> * `SING_BOX_CONFIG_PATH:` `"/var/lib/marznode/sing-box.json"`  

> Specifies whether Sing-Box should automatically restart in case of failure.  
> * `SING_BOX_RESTART_ON_FAILURE:` `"True" / "False"`  

> The interval (in seconds) between automatic restart attempts after Sing-Box encounters an error.  
> * `SING_BOX_RESTART_ON_FAILURE_INTERVAL: "0"`  
>
> **Usage**: If restart attempts are needed, set a specific interval in seconds.  

{{% /steps %}}  
{{% /details %}}


