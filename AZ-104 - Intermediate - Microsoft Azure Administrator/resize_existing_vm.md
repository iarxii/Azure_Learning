Resize an existing VM
We can also resize an existing VM if the workload changes or if it was incorrectly sized at creation. Let's use the first VM we created, SampleVM. Before requesting a resize, we must check to see if the desired size is available in the cluster of which our VM is a part. We can use the vm list-vm-resize-options command:

Azure CLI

Copy
az vm list-vm-resize-options \
    --resource-group "learn-b17fbb0a-5982-4152-aa7d-153a451b3324" \
    --name SampleVM \
    --output table
This command returns a list of all the possible size configurations available in the resource group. If the size we want isn't available in our cluster but is available in the region, we can deallocate the VM. This command stops the running VM and removes it from the current cluster without losing any resources. We can then resize it, which re-creates the VM in a new cluster where the size configuration is available.

 Note

The Microsoft Learn sandbox is limited to a few VM sizes.

To resize a VM, we'll use the vm resize command. For example, perhaps we find our VM is underpowered for the task we want it to perform. We could bump it up to a D2s_v3, where it has 2 vCores and 8 GB of memory. Type this command in Cloud Shell:

Azure CLI

Copy
az vm resize \
    --resource-group "learn-b17fbb0a-5982-4152-aa7d-153a451b3324" \
    --name SampleVM \
    --size Standard_D2s_v3
This command takes a few minutes to reduce the resources of the VM, and once it's done, it returns a new JSON configuration.