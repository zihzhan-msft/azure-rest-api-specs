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
# -------- DO NOT generate and DO generate --------
        - where:
            group: "*"
            op: "*"
          hidden: true

        - where:
            group: Alerts|BandwidthSchedules|Devices|Jobs|Nodes|Orders|Skus
            op: "*"
          hidden: false

        - where:
            group: Devices
            op: GetExtendedInformation|GetNetworkSettings|CreateOrUpdateSecuritySettings|UploadCertificate
          hidden: true

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
            type: Order
            prop: contactInformation|shippingAddress
          cli-flatten: true

        - where:
            group: Orders
            op: CreateOrUpdate#Create
            param: addressLine1|postalCode|city|state|country|contactPerson|companyName|phone|emailList
          required: true

        - where:
            param: addressLine1
          set:
            alias: address_line1

        - where:
            param: addressLine2
          set:
            alias: address_line2

        - where:
            param: addressLine3
          set:
            alias: address_line3

        - where:
            param: postalCode
          set:
            alias: postal_code

        - where:
            param: city
          set:
            alias: city

        - where:
            param: state
          set:
            alias: state

        - where:
            param: country
          set:
            alias: country

        - where:
            param: contactPerson
          set:
            alias: contact_person

        - where:
            param: companyName
          set:
            alias: company_name

        - where:
            param: phone
          set:
            alias: phone

        - where:
            param: emailList
          set:
            alias: email_list

        - where:
            group: Orders
            op: CreateOrUpdate#Create|CreateOrUpdate#Update
            param: status
          set:
            alias: status

        - where:
            group: Orders
            op: CreateOrUpdate#Create|CreateOrUpdate#Update
            param: comments
          set:
            alias: comments
```
