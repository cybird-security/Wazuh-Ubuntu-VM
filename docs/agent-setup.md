# Wazuh Agent Setup and Overview
For this guide, I will be using a Windows Server 2022 VM as a Wazuh agent, since I also want to experiment with Active Directory in the future.
For more information on Wazuh installations, you can view the official documentation here: https://documentation.wazuh.com/current/installation-guide/index.html

## I. Agent Installation

1. Open a web browser and navigate to the Wazuh dashboard by typing in either: `https:<ubuntu-server-ip-here>`. If you followed the guide in the [README](README.md), you can access the dashboard using `https://192.168.1.1`.

2. Use the username `admin` and the password you saved after the Wazuh installation on the Ubuntu Server for more details see section VI of the [README](README.md). Feel free to just save the password as `.txt` file or in the browser password manager for convenience. For optimal security, only store it in a trusted and secure password manager and do not save or place it anywhere that is easily accessible.
  
3. Once you are logged into the dashboard, click on the sidebar button and navigate to `Agents management`, then select `Summary`.

https://github.com/user-attachments/assets/6c81267f-96e7-4b0c-b08f-d7adba7d4480

4. Select `Deploy new agent`, and select the OS you would like to install the agent on. In this case, it is Windows.
   **a.** Enter the IP address of the Ubuntu Server. It is the same one you are using to access this dashboard; if you are following the guide, it should be `192.168.1.1`
   **b.** Give the agent an easily recognizable name. In this case, you can use `winserver-2022`.

5. Open the Windows Terminal/CLI/PowerShell by right-clicking the Windows icon on the taskbar and selecting `Windows PowerShell (Admin)`

https://github.com/user-attachments/assets/f55ffa02-77fb-4be5-9512-21275bce98b0

6. Enter the command Wazuh provides to install the Wazuh agent packages for your Windows instance; it should look something like: `Invoke-WebRequest -Uri https://packages.wazuh.com/4.x/windows/wazuh-agent-4.12.0-1.msi -OutFile $env:tmp\wazuh-agent; msiexec.exe /i $env:tmp\wazuh-agent /q WAZUH_MANAGER='192.168.1.1'`

7. Afterward, to start the agent service and register with the Wazuh manager (the Ubuntu VM we configured previously), run: `NET START WazuhSvc`

Your Windows VM should now be a registered Wazuh agent and viewable on the Wazuh dashboard. Repeat step 3 to verify that the agent appears on the Summary screen.
