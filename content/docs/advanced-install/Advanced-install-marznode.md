---
title: Advanced install Marznode 
linkTitle: "Marznode"
prev: Advanced-install-Marzneshin
---


### Prerequisites
  * *docker*
  * *docker compose*



{{< callout type="info" >}}

 Make sure you have docker installed

 ``` 
 curl -fsSL https://get.docker.com | sh 
 ```
  {{< /callout >}}

  

{{% steps %}}

### Setup your certificate 

   * Create the necessary directory


    
     - ```
        mkdir -p /var/lib/marznode/
       ```


 * And get your certificate from marzneshin settings, place it here:

    - ```
      nano /var/lib/marznode/client.pem
      ```



### Setup some xray config 

  * </sub>Provide some xray config for your node; you could modify it later in the dashboard. We setup the sample config from marznode repository in this case:<sub>

       
    -  ```
       curl -L https://github.com/marzneshin/marznode/raw/master/xray_config.json > /var/lib/marznode/xray_config.json
       ```



### Get Marznode 
      
  *  To clone marznode

     - 
        ```
         git clone https://github.com/marzneshin/marznode
         cd marznode 
         ```
        
                    
### Spin up the container 


  * Execute the following command to get your node up and running

     
    -
       ```
       docker compose -f ./compose.yml up -d 
       ```

{{% /steps %}}
  
{{< callout type="warning" >}}
   
  ### Default Port Configuration
 

  * The default port for connecting the node to the panel is ` 53042 ` . Ensure that your configuration matches this port unless you have explicitly changed it.

  * If you need to customize the port, please update both the node and the panel settings accordingly.

{{< /callout >}}


## Steps to change Marznode port

{{% steps %}}

### Enter the `marznode` directory and open the `compose.yml` file:

   * ```
     cd marznode
     nano compose.yml
     ```

### Add the following variable:

   * ```
       SERVICE_PORT: "53043"
     ```

   Then, save the changes by pressing `Ctrl + X`, followed by `Y` and `Enter`, and exit the editor.


### Restart Docker:

   * ```
     docker compose down && docker compose up -d
       ```
{{% /steps %}}
