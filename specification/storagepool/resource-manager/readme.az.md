## AZ

These settings apply only when `--az` is specified on the command line.

``` yaml $(az)
az:
    extensions: storagepool
    namespace: azure.mgmt.storagepool
    package-name: azure-mgmt-storagepool
az-output-folder: $(azure-cli-extension-folder)/src/storagepool
python-sdk-output-folder: "$(az-output-folder)/azext_storagepool/vendored_sdks/storagepool"
# add additinal configuration here specific for Azure CLI
# refer to the faq.md for more details
```