## CLI

These settings don't need to apply `--cli` on the command line.

``` yaml $(cli)
cli:
  cli-name: desktopvirtualization
  cli-directive:
    - where:
        group: (ActiveApplications|Applications|ApplicationgroupAssignments|Desktops|SessionHosts|StartMenuItems|UserSessions)
      hidden: true
    # - where:
    #     group: ApplicationGroups
    #     op: ListByResourceGroup
    #     param: \$filter
    #   name: list-filter
  test-scenario:
    - name: /HostPools/get/HostPool_List
    - name: /HostPools/get/HostPool_ListByResourceGroup
    - name: /ApplicationGroups/get/ApplicationGroup_List
    - name: /ApplicationGroups/get/ApplicationGroup_ListByResourceGroup
    - name: /Workspaces/get/Workspace_ListByResourceGroup
    - name: /Workspaces/get/Workspace_ListBySubscription
```
