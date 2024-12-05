### Marzneshin Community Docs: Guide to Clone, Install, and Contribute

**Hello!**  
Welcome to the **Marzneshin Community Docs** repository.  
This documentation is developed by the active Marzneshin community to ensure quick, easy access and archiving of information.  
The project is managed using the **Hexo template**, and you are welcome to contribute to its growth.

---

## **How to Contribute**
To participate, follow these steps based on your operating system:

### **Installation and Testing on Windows**
1. Install Chocolatey:
   ```powershell
   Set-ExecutionPolicy Bypass -Scope Process -Force; `
   [System.Net.ServicePointManager]::SecurityProtocol = `
   [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; `
   iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
   ```
2. Verify Chocolatey installation:
   ```powershell
   choco --version
   ```
3. Install Hugo:
   ```powershell
   choco install hugo -y
   ```
4. Confirm Hugo installation:
   ```powershell
   hugo version
   ```
5. (After cloning the repository) Run the project:
   ```powershell
   hugo server --logLevel debug --disableFastRender -p 1313
   ```

### **Installation and Testing on macOS**
1. Install Homebrew:
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```
2. Install Hugo using Homebrew:
   ```bash
   brew install hugo
   ```
3. Verify Hugo installation:
   ```bash
   hugo version
   ```
4. (After cloning the repository) Run the project:
   ```bash
   hugo server --logLevel debug --disableFastRender -p 1313
   ```

### **Installation and Testing on Linux**
1. Install Hugo (using your package manager):
   - For **Debian/Ubuntu**:
     ```bash
     sudo apt-get update
     sudo apt-get install hugo
     ```
   - For **Fedora/RHEL**:
     ```bash
     sudo dnf install hugo
     ```
   - For **Arch Linux**:
     ```bash
     sudo pacman -S hugo
     ```
2. Verify Hugo installation:
   ```bash
   hugo version
   ```
3. (After cloning the repository) Run the project:
   ```bash
   hugo server --logLevel debug --disableFastRender -p 1313
   ```

---

## **If You Can’t Complete This Process**
If you’re unable to install and run Hugo or clone the project, you can submit your proposed content via the **Discussions** section of the GitHub repository. Once reviewed and approved by the team, your content may be added to the documentation.

Thank you for contributing to the Marzneshin community! 🌟