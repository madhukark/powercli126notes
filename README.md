
# PowerCLI 12.6+ with NSX Policy Objects

VMware {code} @ VMware Explore 2022 US



## Authentication:


### On-Prem:
`Connect-NsxServer -Server $NSX_IP -User $NSX_User -Password $NSX_Password`
* -UseRemoteAuthentication for Remote Auth


### VMC:
`$vmcServer = Connect-VmcServer -ApiToken $apiToken`

`$accessToken = $vmcServer.GetAccessToken()`

`$org = Get-VmcOrganization`

`$sddc = Get-VmcSddc -Name $sddcName`


`Connect-NsxVmcServer -AccessToken $accessToken -OrgId $org.Id -SddcId $sddc.Id`


## Search for a specific command
`Get-NsxOperation -Method GET -Path /infra/segments`

`Get-NsxOperation -Method GET -Path '/policy/api/v1/infra/segments'`

`Get-NsxOperation -Method GET -Path '/policy/api/v1/infra/domains/<domain-id>/groups/<group-id>'`

`Get-NsxOperation -Method GET -Path '/infra/domains/{domain-id}/groups/{group-id}'`

`Get-NsxOperation -Method GET -Path '/policy/api/v1/infra/segments*'`


VMC: `Get-NsxOperation -Method Get -Path '/infra/tier-1s/{tier-1-id}/segments'`

PowerCLI 12.6:
* Path is based on API spec
* Accepts wild card
* Has autocomplete

PowerCLI 12.7:
* Path is based on API documentation
* Returns exact match
* Accepts wild card


## Full Details using Get-Help command

* On-Prem: `Get-Help Invoke-ListAllInfraSegments`
* VMC: `Get-Help Invoke-ListSegments`


## Using Get-Command
If you are a bit more comfortable
`Get-Command -Module VMware.Sdk.Nsx.Policy -name Invoke-*Tier0`


## Full Sample Code
https://github.com/vmware-samples/nsx-t/blob/master/powercli/3-Tier-app-v12.6.ps1
