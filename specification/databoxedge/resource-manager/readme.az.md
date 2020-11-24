## AZ

These settings apply only when `--az` is specified on the command line.

``` yaml $(az)
az:
  extensions: data-box-edge
  package-name: azure-mgmt-databoxedge
  namespace: azure.mgmt.databoxedge
az-output-folder: $(azure-cli-extension-folder)/src/databoxedge
python-sdk-output-folder: "$(az-output-folder)/azext_databoxedge/vendored_sdks/databoxedge/v2019_08_01"
extension-mode: preview

directive:
    - where:
        group: data-box-edge job
      set:
        group: data-box-edge

    - where:
        group: data-box-edge node
      set:
        group: data-box-edge

    - where:
        group: data-box-edge sku
      set:
        group: data-box-edge

cli:
    cli-directive:
# -------- rename single command within a group --------
        - where:
            group: Jobs
            op: Get
          name: show_job

        - where:
            group: Nodes
            op: ListByDataBoxEdgeDevice
          name: list_node

        - where:
            group: Skus
            op: List
          name: list_sku

# -------- Order --------
        - where:
            param: contactInformation
          required: true
          cli-flatten: true

        - where:
            param: shippingAddress
          cli-flatten: true

        - where:
            group: Orders
            op: CreateOrUpdate#Create
            param: addressLine1 | postalCode | city | state | country
          required: true
```
