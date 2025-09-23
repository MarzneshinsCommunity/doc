---
title: Varibles
weight: 5
---


In configuration variables, the values `True` and `False` are used to control the status of features and services:  

* **True**: Used to enable a feature or service.  
* **False**: Used to disable a feature or service.  

{{% details title="DEBUG" closed="true" %}}

* This variable is used to toggle the debug mode.  
  - ```bash
      DEBUG: "True"
      ```  
* **True**: Enables debug mode, providing more detailed logs to troubleshoot issues.  
* **False**: Disables debug mode, showing only essential information.  

{{% /details %}}

{{% details title="AUTH_GENERATION_ALGORITHM" closed="true" %}}

* This variable specifies the algorithm used for generating hashes or authentication keys.  

    - ```bash
      AUTH_GENERATION_ALGORITHM: "xxh128"
       ```  
* **xxh128**: A 128-bit version of the xxHash algorithm, known for its high speed and suitability for scenarios requiring fast hash generation with low collision probability.  
* **sha256**: A secure and standard algorithm, ideal for sensitive security applications.  

> **xxh128**: Ideal for environments where speed and performance are critical.  
> **sha256**: Recommended for applications prioritizing security over speed.  

{{% /details %}}


{{% details title="INSECURE" closed="true" %}}

##### To connect the node to the Marzneshin panel via `grpcio` you need to add the following variable:

`INSECURE:` `"True"` / `"False`

```bash
  INSECURE: "True"
  ```
  > This variable enables the connection between the `node` and the `panel` via `grpcio`.

  {{% /details %}}

{{% details title="Managing the XRAY Service" closed="true" %}}  

##### Variables and Descriptions:  

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

{{% /details %}}


{{% details title="Managing the Hysteria Service" closed="true" %}}

##### Variables and Descriptions:  

> A variable to enable or disable the Hysteria service.  
> * `HYSTERIA_ENABLED:` `"True" / "False"`  

> Path to the Hysteria executable used to launch the service.  
> * `HYSTERIA_EXECUTABLE_PATH:` `"/usr/bin/hysteria"`  

> Path to Hysteria’s configuration file containing the key service settings.  
> * `HYSTERIA_CONFIG_PATH:` `"/var/lib/marznode/hysteria.yaml"`  

{{% /details %}}


{{% details title="Managing the Sing-Box Service  " closed="true" %}}

##### Variables and Descriptions:  

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


{{% /details %}}
