```Powershell
# Authenticate using Managed Identity
Connect-AzAccount -Identity

# Ensure you're working in the correct subscription if multiple are accessible
$subscriptionName = 'examplesubscription'
Select-AzSubscription -SubscriptionName $subscriptionName

	# Get all VMs in your subscription
	$vms = Get-AzVM
 
	# Filter VMs by the tag 'exampletag'
	$exampletag = $vms | Where-Object { $_.Tags.Application -eq 'exampletag' }
 
	# Loop through each VM and start it
	foreach ($vm in $exampletag) {
    $vmName = $vm.Name
    $resourceGroupName = $vm.ResourceGroupName
    }
# Define the command to execute the locally stored script
$protectedSettings = @{
    "commandToExecute" = "powershell -ExecutionPolicy Unrestricted -File C:\scripts\examplescript.ps1"
}

# Apply the Custom Script Extension to the VM
Set-AzVMExtension `
    -ResourceGroupName $resourceGroupName `
    -VMName $vmName `
    -Location $location `
    -Name "examplescript" `
    -Publisher "Microsoft.Compute" `
    -ExtensionType "CustomScriptExtension" `
    -TypeHandlerVersion "1.10" `
    -Settings @{} `
    -ProtectedSettings $protectedSettings
