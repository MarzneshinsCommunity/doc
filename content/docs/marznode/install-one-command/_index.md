---
title: One-Command Node Setup
weight: 3
---

{{< callout type="info" >}}
### Requirements
* *GitHub account*
* *Panel certificate client.pem*
* *File content of xray_config.json*
* *File content of compose.yml*
{{< /callout >}}

{{% steps %}}

### Preparing requirements

{{% steps %}}
  ### Log in to your GitHub account, click on your profile (top right corner), then select **Your gists**.
  * Then upload the following files:
    - Panel certificate: `client.pem`
    - Contents of `xray_config.json`
    - Contents of `compose.yml`
  - Place these files here and get their **Raw** links.

  ### In the middle of the page, click the green button **Create a gist**.
   * In the field **Filename including extension...**, enter a file name.
   - Example: `panel-main-client.pem`
   - Paste your panel certificate in the **Enter file contents here** section, then click the green button **Create secret gist** at the bottom.
   - Now your direct link is ready. Click **Raw** in the top-right corner of the file page and copy the link.

  ### Repeat the same steps for the following files and copy their **Raw** links:
  * Contents of `xray_config.json`
  * Contents of `compose.yml`

{{% /steps %}}

### Collecting the commands to execute

{{% details title="Commands" closed="true" %}}

> #### Replace the Raw links you got in the previous steps with:
> - your Raw link/client.pem
> - your Raw link/xray_config.json
> - your Raw link/compose.yml

* Update the server
```bash
apt-get update -y
```

* Install Docker
```bash
curl -fsSL https://get.docker.com | sh
```

* Create the MarzNode directory
```bash
mkdir -p /var/lib/marznode/
```

* Clone the MarzNode repository
```bash
git clone https://github.com/marzneshin/marznode
```

* Download the panel certificate client.pem
```bash
curl -L your-Raw-link/client.pem > /var/lib/marznode/client.pem
```

* Download the contents of xray_config.json
```bash
curl -L your-Raw-link/xray_config.json > /var/lib/marznode/xray_config.json
```

* Change directory to MarzNode
```bash
cd marznode
```

* Download the contents of compose.yml
```bash
curl -L your-Raw-link/compose.yml > compose.yml
```

* Run Docker
```bash
docker compose -f ./compose.yml up -d
```

{{% /details %}}

### Preparing the Final Script 

- Create another gist with a name like:
  - germany-panel-test-install.sh
- Place the commands you prepared in the previous steps inside it.

- The first lines of the file should include these three lines:
```bash
#!/bin/bash
set -e
set -o pipefail
```
- Then enter the commands one by one in order, leaving a blank line between them.

{{< callout type="error" >}}
The commands you put inside this file will be executed on the server one by one from top to bottom.
- Make sure the order of the commands is correct to avoid any issues.
{{< /callout >}}
{{% details title=" Example " closed="true" %}} 

## Sample Content
- germany-panel-test-install.sh
```bash
#!/bin/bash
set -e
set -o pipefail

echo "Updating the server"
apt-get update -y

echo "Installing Docker"
curl -fsSL https://get.docker.com | sh

echo "Creating the MarzNode directory"
mkdir -p /var/lib/marznode/

echo "Cloning the MarzNode repository"
git clone https://github.com/marzneshin/marznode

echo "Downloading the panel certificate client.pem"
curl -L your-Raw-link/client.pem > /var/lib/marznode/client.pem

echo "Downloading the contents of xray_config.json"
curl -L your-Raw-link/xray_config.json > /var/lib/marznode/xray_config.json

echo "Changing directory to MarzNode"
cd marznode

echo "Downloading the contents of compose.yml"
curl -L your-Raw-link/compose.yml > compose.yml

echo "Running Docker"
docker compose -f ./compose.yml up -d

```
{{% /details %}}

### Final Command

- Once you have completed the file `germany-panel-test-install.sh` and obtained the **Raw** link:

  - Replace **your Raw link** in the following command:
  

```bash
curl -L your Raw link | bash
```
 ---

{{% /steps %}}
