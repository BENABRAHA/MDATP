# MDATP SIEM Integration

A few PowerShell scripts that I modified/wrote to test APIs for SIEM integration with IBM QRadar.  Ensure that you can successfully query the APIs before moving to configuring your SIEM.  This will ensure you have the proper connectivity to access the APIs and the proper Azure AD app registration setup before moving on to configuring your SIEM.

How to pull alerts using the MDATP SIEM REST API:<br>
https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/pull-alerts-using-rest-api

Ensure you follow the instructions on how to assign the proper permissions to the app registration for the MDATP Security center API:<br>
https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/api-hello-world

### Azure AD SIEM App Permissions

After you enable SIEM integration in the portal you have to go into AzureAD and add permissions to the registered application to read alerts, this is not done by simply enabling SIEM access.  Go here to assign the " read alert" permission to the registered app:<br>
https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/exposed-apis-create-app-webapp

Once the permissions were assigned I was able to query the APIs successfully.  

### Test SIEM API from Linux

Check the Bash folder for testing directly from Linux hosts!  This may help to eliminate any possible network issues and/or prove that the API can be accessed directly from Linux hosts.

# Alert APIs

There are two APIs that you can query for alerts, the Microsoft Defender API and the MDATP SIEM API.

### Microsoft Defender API
These files test the Defender API in PowerShell/Bash:<br>
Get-Token.ps1/Get-Token.sh<br>
Get-Alerts.ps1/Get-Alerts.sh<br>

### Microsoft Defender SIEM API
These files test the MDATP SIEM API in PowerShell/Bash:<br>
Get-SIEMToken.ps1/Get-SIEMToken.sh<br>
Get-SIEMAlerts.ps1/Get-SIEMAlerts.sh<br>

Run Get-Token first to get your access token, then run Get-Alerts to use the token to query the API.  The PowerShell snips will output the response content in csv and json formats, and the bash scripts will echo the response content to the screen.
