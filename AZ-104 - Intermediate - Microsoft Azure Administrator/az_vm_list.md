Listing images
You can get a list of the available VM images using the following command:

Azure CLI

az vm image list --output table

To filter for specific images by --publisher, --sku or –-offer options
az vm image list --sku Wordpress --output table --all
az vm image list --publisher Microsoft --output table --all

Location-specific images
az vm image list --location eastus --output table