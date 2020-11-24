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

        - where:
            type: OrderProperties
            prop: contactInformation
          flatten: true

        - where:
            type: OrderProperties
            prop: shippingAddress
          flatten: true
```
