Create a Linux virtual machine
Let's create a new Linux virtual machine. Execute the following command in Azure Cloud Shell to create an Ubuntu VM in the West US location.

Azure CLI

az vm create \
  --resource-group "learn-b17fbb0a-5982-4152-aa7d-153a451b3324" \
  --location westus \
  --name SampleVM \
  --image Ubuntu2204 \
  --admin-username azureuser \
  --generate-ssh-keys \
  --size Standard_B1s \
  --verbose


Specify --public-ip-address "" \ if no public ips are needed

---
Azure CLI:
thabang_mposula [ ~ ]$ az vm create \
  --resource-group "learn-b17fbb0a-5982-4152-aa7d-153a451b3324" \
  --location westus \
  --name SampleVM \
  --image Ubuntu2204 \
  --admin-username azureuser \
  --generate-ssh-keys \
  --size Standard_B1s \
  --verbose
The default value of '--size' will be changed to 'Standard_D2s_v5' from 'Standard_DS1_v2' in a future release.
SSH key files '/home/thabang_mposula/.ssh/id_rsa' and '/home/thabang_mposula/.ssh/id_rsa.pub' have been generated under ~/.ssh to allow SSH access to the VM. If using machines without permanent storage, back up your keys to a safe location.
{
  "fqdns": "",
  "id": "/subscriptions/f27a2135-1ae7-44b2-b514-f0b7b1dcbfba/resourceGroups/learn-b17fbb0a-5982-4152-aa7d-153a451b3324/providers/Microsoft.Compute/virtualMachines/SampleVM",
  "location": "westus",
  "macAddress": "00-0D-3A-5C-1E-75",
  "powerState": "VM running",
  "privateIpAddress": "10.0.0.4",
  "publicIpAddress": "172.184.118.251",
  "resourceGroup": "learn-b17fbb0a-5982-4152-aa7d-153a451b3324"
}
thabang_mposula [ ~ ]$ ssh azureuser@172.184.118.251
The authenticity of host '172.184.118.251 (172.184.118.251)' can't be established.
ED25519 key fingerprint is SHA256:5XleodzpFi+rLra8eG6V5TF0OJmOalEyNTWHqB/j+i8.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '172.184.118.251' (ED25519) to the list of known hosts.
Welcome to Ubuntu 22.04.5 LTS (GNU/Linux 6.8.0-1031-azure x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Fri Oct  3 09:34:08 UTC 2025

  System load:  0.06              Processes:             106
  Usage of /:   5.4% of 28.89GB   Users logged in:       0
  Memory usage: 31%               IPv4 address for eth0: 10.0.0.4
  Swap usage:   0%

Expanded Security Maintenance for Applications is not enabled.

0 updates can be applied immediately.

Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status


The list of available updates is more than a week old.
To check for new updates run: sudo apt update


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

azureuser@SampleVM:~$ ps
    PID TTY          TIME CMD
   1851 pts/0    00:00:00 bash
   1872 pts/0    00:00:00 ps
azureuser@SampleVM:~$ ls
azureuser@SampleVM:~$ logout
Connection to 172.184.118.251 closed.
thabang_mposula [ ~ ]$ az vm image list --output table
You are viewing an offline list of images, use --all to retrieve an up-to-date list
Architecture    Offer                         Publisher               Sku                                 Urn                                                                             UrnAlias                 Version
--------------  ----------------------------  ----------------------  ----------------------------------  ------------------------------------------------------------------------------  -----------------------  ---------
x64             CentOS                        OpenLogic               8_5-gen2                            OpenLogic:CentOS:8_5-gen2:latest                                                CentOS85Gen2             latest
x64             debian-11                     Debian                  11-backports-gen2                   Debian:debian-11:11-backports-gen2:latest                                       Debian11                 latest
x64             openSUSE-leap-15-4            SUSE                    gen2                                SUSE:openSUSE-leap-15-4:gen2:latest                                             OpenSuseLeap154Gen2      latest
x64             RHEL                          RedHat                  8-lvm-gen2                          RedHat:RHEL:8-lvm-gen2:latest                                                   RHELRaw8LVMGen2          latest
x64             sles-15-sp5                   SUSE                    gen2                                SUSE:sles-15-sp5:gen2:latest                                                    SuseSles15SP5            latest
x64             0001-com-ubuntu-server-jammy  Canonical               22_04-lts-gen2                      Canonical:0001-com-ubuntu-server-jammy:22_04-lts-gen2:latest                    Ubuntu2204               latest
x64             ubuntu-24_04-lts              Canonical               server                              Canonical:ubuntu-24_04-lts:server:latest                                        Ubuntu2404               latest
x64             ubuntu-24_04-lts              Canonical               ubuntu-pro                          Canonical:ubuntu-24_04-lts:ubuntu-pro:latest                                    Ubuntu2404Pro            latest
x64             flatcar-container-linux-free  kinvolk                 stable-gen2                         kinvolk:flatcar-container-linux-free:stable-gen2:latest                         FlatcarLinuxFreeGen2     latest
x64             WindowsServer                 MicrosoftWindowsServer  2022-datacenter-g2                  MicrosoftWindowsServer:WindowsServer:2022-datacenter-g2:latest                  Win2022Datacenter        latest
x64             WindowsServer                 MicrosoftWindowsServer  2022-datacenter-azure-edition-core  MicrosoftWindowsServer:WindowsServer:2022-datacenter-azure-edition-core:latest  Win2022AzureEditionCore  latest
x64             WindowsServer                 MicrosoftWindowsServer  2019-datacenter-gensecond           MicrosoftWindowsServer:WindowsServer:2019-datacenter-gensecond:latest           Win2019Datacenter        latest
x64             WindowsServer                 MicrosoftWindowsServer  2016-datacenter-gensecond           MicrosoftWindowsServer:WindowsServer:2016-datacenter-gensecond:latest           Win2016Datacenter        latest
x64             WindowsServer                 MicrosoftWindowsServer  2012-R2-Datacenter                  MicrosoftWindowsServer:WindowsServer:2012-R2-Datacenter:latest                  Win2012R2Datacenter      latest
x64             WindowsServer                 MicrosoftWindowsServer  2012-Datacenter                     MicrosoftWindowsServer:WindowsServer:2012-Datacenter:latest                     Win2012Datacenter        latest
thabang_mposula [ ~ ]$ 