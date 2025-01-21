# Input bindings are passed in via param block.
param($Request)

# Connect to Exchange Online
$UserCredential = Get-Credential -Message "Enter your Exchange Online credentials"
Connect-ExchangeOnline -Credential $UserCredential

# Extract the user UPN from the request body
$TheUserUPN = $Request.Body.UserUpn

# Convert mailbox to shared
Set-Mailbox -Identity $TheUserUPN -Type Shared -LitigationHoldEnabled $true

# Return a response
@{
    status = "success"
    message = "Mailbox converted to shared and litigation hold enabled."
} | ConvertTo-Json
