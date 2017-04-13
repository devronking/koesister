Software Testing Code Snippets
==========================



#### <i class="icon-pencil"></i> Kickoff Jenkins from Octopus Deploy - Powershell
----------
```sh
$user = "Administrator" 
$pass = "Password" 
$pair = "${user}:${pass}" 
$bytes = [System.Text.Encoding]::ASCII.GetBytes($pair) 
$base64 = [System.Convert]::ToBase64String($bytes) 
$basicAuthValue = "Basic $base64" $headers = @{ Authorization = $basicAuthValue } Invoke-WebRequest -uri "http://jenkinsserver:port/job/myproject/build?token=runmyprojectrun" -Headers $headers
```


#### <i class="icon-pencil"></i> Get Jenkins Job Results - Powershell
----------
```sh
$failcount = $json.actions.failCount
```


#### <i class="icon-pencil"></i> Check if API is up - Powershell
----------
```sh
$check = 'true'
try { $response = Invoke-WebRequest http://jenkinsserver:port/v1-Alpha/api/Get/Creditors } catch {
      $check = 'false'
         Write-Host "API is down" 
      exit 1
         }
If ($check -eq 'true')
{
    Write-Host "API is up"
    exit 0
} 
```


#### <i class="icon-pencil"></i> Return XML field as column - SQL Query
----------
```sh
select xmlfield.value('(/response//data/TransactionId/node())[1]', 'varchar(50)') 
as TransactionId from (select cast(REPLACE(Metadata, 'utf-8', 'utf-16') as xml) 
as xmlfield from dbo.table1 Ev join table2 Cor 
on Cor.MandateRequestId = Ev.MandateRequestId where EventType = 30 
and Cor.CorrelationId = '12345') Temp
```
