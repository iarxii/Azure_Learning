Exercise - Sizing VMs properly
Completed
100 XP
10 minutes
Sandbox activated! Time remaining: 
You have used 2 of 10 sandboxes for today. More sandboxes will be available tomorrow.

Virtual machines must be sized appropriately for the expected work. A VM without the correct amount of memory or CPU will fail under load or run too slowly to be effective.

Predefined VM sizes
When you create a virtual machine, you can supply a VM size value that determines the amount of compute resources devoted to the VM, including CPU, GPU, and memory made available to the virtual machine from Azure.

Azure defines a set of predefined VM sizes for Linux and Windows from which to choose based on the expected usage.

Type	Sizes	Description
General purpose	Dsv3, Dv3, DSv2, Dv2, DS, D, Av2, A0-7	Balanced CPU-to-memory. Ideal for dev/test and small to medium applications and data solutions.
Compute optimized	Fs, F	High CPU-to-memory. Good for medium-traffic applications, network appliances, and batch processes.
Memory optimized	Esv3, Ev3, M, GS, G, DSv2, DS, Dv2, D	High memory-to-core. Great for relational databases, medium to large caches, and in-memory analytics.
Storage optimized	Ls	High disk throughput and IO. Ideal for big data, SQL, and NoSQL databases.
GPU optimized	NV, NC	Specialized VMs targeted for heavy graphic rendering and video editing.
High performance	H, A8-11	Our most powerful CPU VMs with optional high-throughput network interfaces (RDMA).
The available sizes change based on the region in which you're creating the VM. You can get a list of the available sizes using the vm list-sizes command. Try typing the following command into Azure Cloud Shell:

Azure CLI

Copy
az vm list-sizes --location eastus --output table
Here's an abbreviated response for eastus:

Output

Copy
  MaxDataDiskCount    MemoryInMb  Name                      NumberOfCores    OsDiskSizeInMb    ResourceDiskSizeInMb
------------------  ------------  ----------------------  ---------------  ----------------  ----------------------
                 2          2048  Standard_B1ms                         1           1047552                    4096
                 2          1024  Standard_B1s                          1           1047552                    2048
                 4          8192  Standard_B2ms                         2           1047552                   16384
                 4          4096  Standard_B2s                          2           1047552                    8192
                 8         16384  Standard_B4ms                         4           1047552                   32768
                16         32768  Standard_B8ms                         8           1047552                   65536
                 4          3584  Standard_DS1_v2                       1           1047552                    7168
                 8          7168  Standard_DS2_v2                       2           1047552                   14336
                16         14336  Standard_DS3_v2                       4           1047552                   28672
                32         28672  Standard_DS4_v2                       8           1047552                   57344
                64         57344  Standard_DS5_v2                      16           1047552                  114688
        ....
                64       3891200  Standard_M128-32ms                  128           1047552                 4096000
                64       3891200  Standard_M128-64ms                  128           1047552                 4096000
                64       3891200  Standard_M128ms                     128           1047552                 4096000
                64       2048000  Standard_M128s                      128           1047552                 4096000
                64       1024000  Standard_M64                         64           1047552                 8192000
                64       1792000  Standard_M64m                        64           1047552                 8192000
                64       2048000  Standard_M128                       128           1047552                16384000
                64       3891200  Standard_M128m                      128           1047552                16384000
Specify a size during VM creation
We didn't specify a size when we created our VM, so Azure selected a default general-purpose size for us. However, we can specify the size as part of the vm create command using the --size parameter. For example, you could use the following command to create a two-core virtual machine:

Azure CLI

Copy
az vm create \
    --resource-group "learn-b17fbb0a-5982-4152-aa7d-153a451b3324" \
    --name SampleVM2 \
    --image Ubuntu2204 \
    --admin-username azureuser \
    --generate-ssh-keys \
    --verbose \
    --size "Standard_DS2_v2"
 Warning

Your subscription tier enforces limits on how many resources you can create, as well as the total size of those resources. Quota limits depend upon your subscription type and region. The Azure CLI lets you know when you exceed this limit with a Quota Exceeded error. If you hit this error in your own paid subscription, you can request to raise the limits associated with your paid subscription (up to 10,000 vCPUs) through a free online request.