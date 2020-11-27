## CLI

These settings apply only when `--cli` is specified on the command line.

``` yaml $(cli)
cli:
  cli-name: databoxedge
  package-name: azure-mgmt-databoxedge
  namespace: azure.mgmt.databoxedge
  cli-directive:
    - where:
        group: StorageAccountCredentials
        op: CreateOrUpdate.*
      hidden: true
    - where:
        group: StorageAccounts
        op: CreateOrUpdate.*
      hidden: true
  test-scenario:
      general:
        - name: OperationsGet
        - name: ListSkus
        - name: ListAvailableSkus
        - name: OperationsStatusGet
        - name: JobsGet
      device_general:
        - name: DataBoxEdgeDevicePut
        - name: DataBoxEdgeDeviceGetByName
        - name: DataBoxEdgeDeviceGetByResourceGroup
        - name: DataBoxEdgeDeviceGetBySubscription
        - name: DataBoxEdgeDevicePatch
        - name: DataBoxEdgeDeviceGetByName
        - name: DataBoxEdgeDeviceDelete
      device_manage:
        - name: NodesGetAllInDevice
        - name: ScanForUpdatesPost
        - name: UpdateSummaryGet
        - name: DownloadUpdatesPost
        - name: InstallUpdatesPost
        - name: AlertGetAllInDevice
        - name: AlertGet
        - name: NetworkSettingsGet
        - name: ExtendedInfoPost
        - name: CreateOrUpdateSecuritySettings
        - name: UploadCertificatePost
      order:
        - name: OrderPut
        - name: OrderGet
        - name: OrderGetAllInDevice
        - name: OrderDelete
      bandwidth_schedule:
        - name: BandwidthSchedulePut
        - name: BandwidthScheduleGet
        - name: BandwidthScheduleGetAllInDevice
        - name: BandwidthScheduleDelete
      user:
        - name: UserPut
        - name: UserGet
        - name: UserGetAllInDevice
        - name: UserDelete
      role:
        - name: RolePut
        - name: RoleGet
        - name: RoleGetAllInDevice
        - name: RoleDelete
      share:
        - name: SharePut
        - name: ShareGet
        - name: ShareGetAllInDevice
        - name: ShareRefreshPost
        - name: ShareDelete
      trigger:
        - name: TriggerPut
        - name: TriggerGet
        - name: TriggerGetAllInDevice
        - name: TriggerDelete
      storage_account:
        - name: StorageAccountPut
        - name: StorageAccountGet
        - name: StorageAccountGetAllInDevice
        - name: StorageAccountDelete
      sac:
        - name: SACPut
        - name: SACGet
        - name: SACGetAllInDevice
        - name: SACDelete
      container:
        - name: ContainerPut
        - name: ContainerGet
        - name: ContainerListAllInDevice
        - name: ContainerRefresh
        - name: ContainerDelete
```