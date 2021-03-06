# Windows Subsystem for Linux (WSL) Setup

This repo documents the process for setting up a development environment using the Windows Subsystem for Linux.

1. Install [Visual Studio Code](https://code.visualstudio.com/) on Windows machine

2. Install WSL

   - As instructed [here](https://docs.microsoft.com/en-us/windows/wsl/install-win10):
     - From the start menu search `powershell`, right-click and select `run as administrator`
     - Enter the command `Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux`
     - Restart when prompted

3. Install Ubuntu version

   - Open Microsoft Store
   - Search "Ubuntu"
   - Select and install latest version (currently [Ubuntu 18.04 LTS](https://www.microsoft.com/store/productId/9N9TNGVNDL3Q))

4. Open Ubuntu from Start Menu

   - Wait for install to complete
   - Enter Ubuntu username and password when prompted

5. Optional - Set Alias Commands

   - Alias commands are useful to save time if similar commands are run frequently
   - In Ubuntu shell, run the command `nano ~/.bashrc` (to use nano text editor, can be any)
   - At end of file, add: `alias projects='cd /documents/projects`
   - Save the changes made to `.bashrc` file
   - Run the command `source ~/.bashrc`
   - Now to navigate to `/documents/projects` use the command `projects`

6. Setup GitHub SSH Keys

   - Follow the GitHub [instructions](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) to create a new SSH key in Ubuntu shell
     - Once complete (SSH key is generated, stored in the default location and using a secure passphrase), view the public key using `cat .ssh/id_rsa.pub`
   - Copy the public SSH key to clipboard
   - Save it as a new key on GitHub (instructions [here](https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account) if needed)

7. Fix Permissions

   - Need to allow WSL permissions to change and edit files located within `/mnt/`
   - Follow instructions [here](https://askubuntu.com/questions/911804/ubuntu-for-windows-10-all-files-are-own-by-root-and-i-cannot-change-it)
     - Use command `sudo nano /etc/wsl.conf` to open and edit the file

8. Install NVM

   - Install Node Version Manager (NVM) from [here](https://github.com/nvm-sh/nvm#installing-and-updating)
   - Use NVM to install desired version of Node.js: `nvm install vXX.XX.X` (current LTS version is 12.16.0)
   - Set the Node version to use: `nvm use 12.16.0` (for example)
   - Set the default: `nvm alias default 12.16.0` (for example)

9. Install VS Code extension

   - Install `ms-vscode-remote.remote-wsl` extension in VS Code

10. Ready to work
    - Work flow for developing is as follows:
      - Power up Windows machine
      - Open Ubuntu subsystem
      - Use alias `projects` (or whichever was set), or `cd` to the desired folder
      - Once in project folder `code .` command to open VS Code
        - This will open VS Code in the current directory, editing on Ubuntu 18.04
    - _Note_ - it is not advised to use the windows file system (`/mnt` folder) when using WSL. Instead it is recommended to use the linux file system, as it is [much faster](https://dev.to/kleeut/why-is-wsl2-so-slow-4n3i).
