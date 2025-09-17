# Windows Server 2022 Hardening with SCT and PowerStig
In this guide, we are going to harden Windows Server 2022 using Microsoft's Secure Configuration Toolkit (SCT) and PowerStig, a CLI utility that generates a Desired State Configuration (DSC). The SCT will create the secure baseline and PowerStig and the resulting DSC config will harden the system even further.

## I. Preqrequisites

1. A Windows Server 2022 system (I am using a VM) and the Roles and Features you would like to run on the server (AD Domain Services, DHCP/DNS Servers, etc.). Given this is building off the guide for configuring Wazuh, you should complete the guides in the [README](README.md) and [agent-setup](agent-setup.md) so you can quantitatively assess the results of our hardening efforts.

2. Download Microsoft's SCT for the initial baseline: https://www.microsoft.com/en-us/download/details.aspx?id=55319

3. Install the PowerStig modules. Run in PowerShell: `Install-Module -Name PowerSTIG`
