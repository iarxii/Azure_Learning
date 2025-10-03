Stop a VM
We can stop a running VM with the vm stop command. You must pass the name and resource group or the unique ID for the VM:

Azure CLI

Copy
az vm stop \
    --name SampleVM \
    --resource-group "learn-b17fbb0a-5982-4152-aa7d-153a451b3324"
You can verify the VM has stopped by attempting to ping the public IP address, using ssh, or through the vm get-instance-view command. This final approach returns the same basic data as vm show, but includes details about the instance itself. Try entering the following command into Azure Cloud Shell to see the current running state of your VM:

Azure CLI

Copy
az vm get-instance-view \
    --name SampleVM \
    --resource-group "learn-b17fbb0a-5982-4152-aa7d-153a451b3324" \
    --query "instanceView.statuses[?starts_with(code, 'PowerState/')].displayStatus" -o tsv
This command should return VM stopped as the result.

Start a VM
We can do the reverse through the vm start command.

Azure CLI

Copy
az vm start \
    --name SampleVM \
    --resource-group "learn-b17fbb0a-5982-4152-aa7d-153a451b3324"
This command starts a stopped VM. You can verify it through the vm get-instance-view query you used in the last section, which should now return VM running.

Restart a VM
Finally, we can restart a VM if we've made changes that require a reboot by running the vm restart command. You can add the --no-wait flag if you want the Azure CLI to return immediately without waiting for the VM to reboot.

CLI ------------------------------------------

thabang_mposula [ ~ ]$ az vm stop --name SampleVM --resource-group "learn-b17fbb0a-5982-4152-aa7d-153a451b3324"
About to power off the specified VM...
It will continue to be billed. To deallocate a VM, run: az vm deallocate.
thabang_mposula [ ~ ]$ az vm get-instance-view --name SampleVM --resource-group "learn-b17fbb0a-5982-4152-aa7d-153a451b3324" --query "instanceView.statuses[?starts_with(code, 'PowerState/')].displayStatus" -o tsv
VM stopped
thabang_mposula [ ~ ]$ az vm get-instance-view --name SampleVM --resource-group "learn-b17fbb0a-5982-4152-aa7d-153a451b3324" --query "instanceView.statuses[?starts_with(code, 'PowerState/')].displayStatus" -o table
Result
----------
VM stopped
thabang_mposula [ ~ ]$ az vm start --name SampleVM --resource-group "learn-b17fbb0a-5982-4152-aa7d-153a451b3324"
thabang_mposula [ ~ ]$ az vm get-instance-view --name SampleVM --resource-group "learn-b17fbb0a-5982-4152-aa7d-153a451b3324" --query "instanceView.statuses[?starts_with(code, 'PowerState/')].displayStatus" -o table
Result
----------
VM running
