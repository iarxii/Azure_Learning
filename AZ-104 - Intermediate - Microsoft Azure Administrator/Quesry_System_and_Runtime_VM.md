thabang_mposula [ ~ ]$ az vm list
[
  {
    "etag": "\"1\"",
    "hardwareProfile": {
      "vmSize": "Standard_B1s"
    },
    "id": "/subscriptions/f27a2135-1ae7-44b2-b514-f0b7b1dcbfba/resourceGroups/LEARN-B17FBB0A-5982-4152-AA7D-153A451B3324/providers/Microsoft.Compute/virtualMachines/SampleVM",
    "location": "westus",
    "name": "SampleVM",
    "networkProfile": {
      "networkInterfaces": [
        {
          "id": "/subscriptions/f27a2135-1ae7-44b2-b514-f0b7b1dcbfba/resourceGroups/learn-b17fbb0a-5982-4152-aa7d-153a451b3324/providers/Microsoft.Network/networkInterfaces/SampleVMVMNic",
          "resourceGroup": "learn-b17fbb0a-5982-4152-aa7d-153a451b3324"
        }
      ]
    },
    "osProfile": {
      "adminUsername": "azureuser",
      "allowExtensionOperations": true,
      "computerName": "SampleVM",
      "linuxConfiguration": {
        "disablePasswordAuthentication": true,
        "patchSettings": {
          "assessmentMode": "ImageDefault",
          "patchMode": "ImageDefault"
        },
        "provisionVMAgent": true,
        "ssh": {
          "publicKeys": [
            {
              "keyData": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDV6QFK6rL8P+Ikn1aaxoj+kDv5WQqxfgLBBPis3w05V5/FYJ1y3Kxamu+aeFHPUPEU8HPA9w7QLWVEi+JF4Tf15dUu6W00jIbDh64AdqknE6aPbJo/kZ+BrLJEjPcSIK4AJd8vnh6n+3O0GBLsgqppuZKtZiJfB9WLG2Z7SAYe4KDgVVlYHDBq/0bEKrVZ/jaAY4x6KExnzayZzUKF3/oJMxbUv96jlNhGkf8ZgsOgPHdEDTppmxS3g4pZhzDAAj0H5+xVtHjiGIboHHj7fkUJzGvC+rGzyaLCBUuaXErFE+PGYYGWYV11a5WNGR8tlkLkjjNJrZP9xJiLEASOk8PD",
              "path": "/home/azureuser/.ssh/authorized_keys"
            }
          ]
        }
      },
      "requireGuestProvisionSignal": true,
      "secrets": []
    },
    "provisioningState": "Succeeded",
    "resourceGroup": "LEARN-B17FBB0A-5982-4152-AA7D-153A451B3324",
    "resources": [
      {
        "id": "/subscriptions/f27a2135-1ae7-44b2-b514-f0b7b1dcbfba/resourceGroups/LEARN-B17FBB0A-5982-4152-AA7D-153A451B3324/providers/Microsoft.Compute/virtualMachines/SampleVM/extensions/AzureMonitorLinuxAgent",
        "resourceGroup": "LEARN-B17FBB0A-5982-4152-AA7D-153A451B3324"
      }
    ],
    "securityProfile": {
      "securityType": "TrustedLaunch",
      "uefiSettings": {
        "secureBootEnabled": true,
        "vTpmEnabled": true
      }
    },
    "storageProfile": {
      "dataDisks": [],
      "diskControllerType": "SCSI",
      "imageReference": {
        "exactVersion": "22.04.202507300",
        "offer": "0001-com-ubuntu-server-jammy",
        "publisher": "Canonical",
        "sku": "22_04-lts-gen2",
        "version": "latest"
      },
      "osDisk": {
        "caching": "ReadWrite",
        "createOption": "FromImage",
        "deleteOption": "Detach",
        "diskSizeGB": 30,
        "managedDisk": {
          "id": "/subscriptions/f27a2135-1ae7-44b2-b514-f0b7b1dcbfba/resourceGroups/learn-b17fbb0a-5982-4152-aa7d-153a451b3324/providers/Microsoft.Compute/disks/SampleVM_disk1_87af04dac49c4b3fa488652cfa2b0109",
          "resourceGroup": "learn-b17fbb0a-5982-4152-aa7d-153a451b3324",
          "storageAccountType": "Premium_LRS"
        },
        "name": "SampleVM_disk1_87af04dac49c4b3fa488652cfa2b0109",
        "osType": "Linux"
      }
    },
    "tags": {},
    "timeCreated": "2025-10-03T09:31:37.6339389+00:00",
    "type": "Microsoft.Compute/virtualMachines",
    "vmId": "7cf95855-1132-4479-96b4-2e225aba7084"
  }
]
thabang_mposula [ ~ ]$ az vm list --output table
Name      ResourceGroup                               Location
--------  ------------------------------------------  ----------
SampleVM  LEARN-B17FBB0A-5982-4152-AA7D-153A451B3324  westus

--- Along with table, you can specify json (the default), jsonc (colorized JSON), or tsv (Tab-Separated Values). Try a few variations with the preceding command to see the difference.
az vm list --output table
az vm list --output json
az vm list --output jsconc
az vm list --output tsv

--- List ip addresses
thabang_mposula [ ~ ]$ az vm list-ip-addresses -n SampleVM -o table
VirtualMachine    PublicIPAddresses    PrivateIPAddresses
----------------  -------------------  --------------------
SampleVM          172.184.118.251      10.0.0.4

 Tip

Notice that we're using a shorthand syntax for the --output flag as -o. You can shorten most parameters to Azure CLI commands to a single dash and letter. For example, you can shorten --name to -n and --resource-group to -g. This is handy for entering keyboard characters, but we recommend using the full option name in scripts for clarity. Check the documentation for details about each command.

---Get VM details
We can get more detailed information about a specific virtual machine by name or ID running the vm show command.

thabang_mposula [ ~ ]$ az vm show --resource-group "learn-b17fbb0a-5982-4152-aa7d-153a451b3324" --name SampleVM -o jsonc
{
  "additionalCapabilities": null,
  "applicationProfile": null,
  "availabilitySet": null,
  "billingProfile": null,
  "capacityReservation": null,
  "diagnosticsProfile": null,
  "etag": "\"1\"",
  "evictionPolicy": null,
  "extendedLocation": null,
  "extensionsTimeBudget": null,
  "hardwareProfile": {
    "vmSize": "Standard_B1s",
    "vmSizeProperties": null
  },
  "host": null,
  "hostGroup": null,
  "id": "/subscriptions/f27a2135-1ae7-44b2-b514-f0b7b1dcbfba/resourceGroups/learn-b17fbb0a-5982-4152-aa7d-153a451b3324/providers/Microsoft.Compute/virtualMachines/SampleVM",
  "identity": null,
  "instanceView": null,
  "licenseType": null,
  "location": "westus",
  "managedBy": null,
  "name": "SampleVM",
  "networkProfile": {
    "networkApiVersion": null,
    "networkInterfaceConfigurations": null,
    "networkInterfaces": [
      {
        "deleteOption": null,
        "id": "/subscriptions/f27a2135-1ae7-44b2-b514-f0b7b1dcbfba/resourceGroups/learn-b17fbb0a-5982-4152-aa7d-153a451b3324/providers/Microsoft.Network/networkInterfaces/SampleVMVMNic",
        "primary": null,
        "resourceGroup": "learn-b17fbb0a-5982-4152-aa7d-153a451b3324"
      }
    ]
  },
  "osProfile": {
    "adminPassword": null,
    "adminUsername": "azureuser",
    "allowExtensionOperations": true,
    "computerName": "SampleVM",
    "customData": null,
    "linuxConfiguration": {
      "disablePasswordAuthentication": true,
      "enableVmAgentPlatformUpdates": null,
      "patchSettings": {
        "assessmentMode": "ImageDefault",
        "automaticByPlatformSettings": null,
        "patchMode": "ImageDefault"
      },
      "provisionVmAgent": true,
      "ssh": {
        "publicKeys": [
          {
            "keyData": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDV6QFK6rL8P+Ikn1aaxoj+kDv5WQqxfgLBBPis3w05V5/FYJ1y3Kxamu+aeFHPUPEU8HPA9w7QLWVEi+JF4Tf15dUu6W00jIbDh64AdqknE6aPbJo/kZ+BrLJEjPcSIK4AJd8vnh6n+3O0GBLsgqppuZKtZiJfB9WLG2Z7SAYe4KDgVVlYHDBq/0bEKrVZ/jaAY4x6KExnzayZzUKF3/oJMxbUv96jlNhGkf8ZgsOgPHdEDTppmxS3g4pZhzDAAj0H5+xVtHjiGIboHHj7fkUJzGvC+rGzyaLCBUuaXErFE+PGYYGWYV11a5WNGR8tlkLkjjNJrZP9xJiLEASOk8PD",
            "path": "/home/azureuser/.ssh/authorized_keys"
          }
        ]
      }
    },
    "requireGuestProvisionSignal": true,
    "secrets": [],
    "windowsConfiguration": null
  },
  "placement": null,
  "plan": null,
  "platformFaultDomain": null,
  "priority": null,
  "provisioningState": "Succeeded",
  "proximityPlacementGroup": null,
  "resourceGroup": "learn-b17fbb0a-5982-4152-aa7d-153a451b3324",
  "resources": [
    {
      "autoUpgradeMinorVersion": true,
      "enableAutomaticUpgrade": true,
      "forceUpdateTag": null,
      "id": "/subscriptions/f27a2135-1ae7-44b2-b514-f0b7b1dcbfba/resourceGroups/learn-b17fbb0a-5982-4152-aa7d-153a451b3324/providers/Microsoft.Compute/virtualMachines/SampleVM/extensions/AzureMonitorLinuxAgent",
      "instanceView": null,
      "location": "westus",
      "name": "AzureMonitorLinuxAgent",
      "protectedSettings": null,
      "protectedSettingsFromKeyVault": null,
      "provisionAfterExtensions": null,
      "provisioningState": "Succeeded",
      "publisher": "Microsoft.Azure.Monitor",
      "resourceGroup": "learn-b17fbb0a-5982-4152-aa7d-153a451b3324",
      "settings": {
        "authentication": {
          "managedIdentity": {
            "identifier-name": "mi_res_id",
            "identifier-value": "/subscriptions/f27a2135-1ae7-44b2-b514-f0b7b1dcbfba/resourceGroups/built-in-identity-rg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/built-in-identity-westus"
          }
        }
      },
      "suppressFailures": null,
      "tags": null,
      "type": "Microsoft.Compute/virtualMachines/extensions",
      "typeHandlerVersion": "1.36",
      "typePropertiesType": "AzureMonitorLinuxAgent"
    }
  ],
  "scheduledEventsPolicy": null,
  "scheduledEventsProfile": null,
  "securityProfile": {
    "encryptionAtHost": null,
    "encryptionIdentity": null,
    "proxyAgentSettings": null,
    "securityType": "TrustedLaunch",
    "uefiSettings": {
      "secureBootEnabled": true,
      "vTpmEnabled": true
    }
  },
  "storageProfile": {
    "alignRegionalDisksToVmZone": null,
    "dataDisks": [],
    "diskControllerType": "SCSI",
    "imageReference": {
      "communityGalleryImageId": null,
      "exactVersion": "22.04.202507300",
      "id": null,
      "offer": "0001-com-ubuntu-server-jammy",
      "publisher": "Canonical",
      "sharedGalleryImageId": null,
      "sku": "22_04-lts-gen2",
      "version": "latest"
    },
    "osDisk": {
      "caching": "ReadWrite",
      "createOption": "FromImage",
      "deleteOption": "Detach",
      "diffDiskSettings": null,
      "diskSizeGb": 30,
      "encryptionSettings": null,
      "image": null,
      "managedDisk": {
        "diskEncryptionSet": null,
        "id": "/subscriptions/f27a2135-1ae7-44b2-b514-f0b7b1dcbfba/resourceGroups/learn-b17fbb0a-5982-4152-aa7d-153a451b3324/providers/Microsoft.Compute/disks/SampleVM_disk1_87af04dac49c4b3fa488652cfa2b0109",
        "resourceGroup": "learn-b17fbb0a-5982-4152-aa7d-153a451b3324",
        "securityProfile": null,
        "storageAccountType": "Premium_LRS"
      },
      "name": "SampleVM_disk1_87af04dac49c4b3fa488652cfa2b0109",
      "osType": "Linux",
      "vhd": null,
      "writeAcceleratorEnabled": null
    }
  },
  "tags": {},
  "timeCreated": "2025-10-03T09:31:37.633938+00:00",
  "type": "Microsoft.Compute/virtualMachines",
  "userData": null,
  "virtualMachineScaleSet": null,
  "vmId": "7cf95855-1132-4479-96b4-2e225aba7084",
  "zones": null
}

--- Filter your Azure CLI queries
With a basic understanding of JMES queries, we can add filters to the data returned by queries like the vm show command. For example, we can retrieve the admin username:

thabang_mposula [ ~ ]$ az vm show --resource-group "learn-b17fbb0a-5982-4152-aa7d-153a451b3324" --name SampleVM --query "osProfile.adminUsername"
"azureuser"
thabang_mposula [ ~ ]$ az vm show --resource-group "learn-b17fbb0a-5982-4152-aa7d-153a451b3324" --name SampleVM --query hardwareProfile.vmSize
"Standard_B1s"
thabang_mposula [ ~ ]$ az vm show --resource-group "learn-b17fbb0a-5982-4152-aa7d-153a451b3324" --name SampleVM --query "networkProfile.networkInterfaces[].id"
[
  "/subscriptions/f27a2135-1ae7-44b2-b514-f0b7b1dcbfba/resourceGroups/learn-b17fbb0a-5982-4152-aa7d-153a451b3324/providers/Microsoft.Network/networkInterfaces/SampleVMVMNic"
]
thabang_mposula [ ~ ]$ az vm show --resource-group "learn-b17fbb0a-5982-4152-aa7d-153a451b3324" --name SampleVM --query "networkProfile.networkInterfaces[].id" -o tsv
/subscriptions/f27a2135-1ae7-44b2-b514-f0b7b1dcbfba/resourceGroups/learn-b17fbb0a-5982-4152-aa7d-153a451b3324/providers/Microsoft.Network/networkInterfaces/SampleVMVMNic