# Windows Server 2022 Hardening with SCT and PowerStig
In this guide, we are going to harden Windows Server 2022 using Microsoft's Secure Configuration Toolkit (SCT) and DoD (Department of Defense) STIGs. The SCT will create the secure baseline and the STIGs will harden the system even further.

## I. Preqrequisites

1. A Windows Server 2022 system (I am using a VM) and the Roles and Features you would like to run on the server (AD Domain Services, DHCP/DNS Servers, etc.). Given this is building off the guide for configuring Wazuh, you should complete the guides in the [README](/README.md) and [agent-setup](agent-setup.md) so you can quantitatively assess the results of our hardening efforts.

    **a.** After installing the Role and Features of my choosing and promoting my Server to a domain controller, I lost Internet access. I did not find a quick solution to the issue, but for the sake of this guide we will pre-install everything we need before enabling Active Directory and its various services.

2. Download Microsoft's SCT for the initial baseline: [https://www.microsoft.com/en-us/download/details.aspx?id=55319](https://www.microsoft.com/en-us/download/details.aspx?id=55319)

   **a.** You only need to download the files for Windows Server 2022 and the Policy Analyzer tool. The `.zip` includes Group Policy configurations for different instances of Server 2022, and for the purpose of this guide, I will be using the Domain Controller baseline. The Policy Analyzer identifies GPO redundancies, differences, and can export results for viewing.

3. Install the following tools from [cyber.mil](https://www.cyber.mil/):

    **a.** [https://www.cyber.mil/stigs/srg-stig-tools/](https://www.cyber.mil/stigs/srg-stig-tools/) - `STIG Viewer 3.6.0-Win64 msi` under STIG Viewer 3.x.

    **b.** [https://www.cyber.mil/stigs/SCAP](https://www.cyber.mil/stigs/srg-stig-tools/) - `Microsoft Windows Server 2022 STIG SCAP Benchmark - Ver 2, Rel 5` under SCAP 1.3 Content and `SCC 5.12.1 Windows` under SCAP Tools.

4. Once you have all of the above installed, extract them in a directory of your choosing. I am extracting them in the `Downloads` directory.

5. Navigate to the extracted SCAP Tool folder. It should have a file name like `scc-5.12.1_Windows_bundle`. Run the `SCC_5.X_Windows_Setup` tool.
