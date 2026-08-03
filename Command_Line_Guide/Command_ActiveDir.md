# Most used Active Directory commands
(PowerShell AD module + native Windows tools — run from a domain-joined machine or Domain Controller with RSAT/ActiveDirectory module installed)

**Domain & Connectivity basics**
```
1. Current domain -> Get-ADDomain
2. Current forest -> Get-ADForest
3. Domain controllers list -> Get-ADDomainController -Filter *
4. Test domain connectivity -> Test-ComputerSecureChannel
5. Current logged in user's domain info -> whoami /fqdn
6. Show domain trusts -> Get-ADTrust -Filter *
7. Domain functional level -> (Get-ADDomain).DomainMode
```

**User account related**
```
1. Create a user -> New-ADUser -Name "John Doe" -SamAccountName jdoe
2. Get a user's info -> Get-ADUser jdoe -Properties *
3. Search users by filter -> Get-ADUser -Filter "Name -like '*john*'"
4. Modify a user -> Set-ADUser jdoe -Department "IT"
5. Remove a user -> Remove-ADUser jdoe
6. Disable a user -> Disable-ADAccount jdoe
7. Enable a user -> Enable-ADAccount jdoe
8. Unlock a user -> Unlock-ADAccount jdoe
9. Reset a password -> Set-ADAccountPassword jdoe -Reset
10. Find locked out accounts -> Search-ADAccount -LockedOut
```

**Group related**
```
1. Create a group -> New-ADGroup -Name "IT-Team" -GroupScope Global
2. Get a group's info -> Get-ADGroup "IT-Team" -Properties *
3. List group members -> Get-ADGroupMember "IT-Team"
4. Add a user to group -> Add-ADGroupMember "IT-Team" -Members jdoe
5. Remove a user from group -> Remove-ADGroupMember "IT-Team" -Members jdoe
6. Find groups a user belongs to -> Get-ADPrincipalGroupMembership jdoe
7. Remove a group -> Remove-ADGroup "IT-Team"
```

**Computer object related**
```
1. Get a computer's info -> Get-ADComputer PC01 -Properties *
2. Search computers by filter -> Get-ADComputer -Filter "Name -like 'PC*'"
3. Find stale/inactive computers -> Search-ADAccount -AccountInactive -ComputersOnly -TimeSpan 90.00:00:00
4. Disable a computer account -> Disable-ADAccount -Identity PC01$
5. Remove a computer object -> Remove-ADComputer PC01
6. Move a computer to another OU -> Move-ADObject -Identity <DN> -TargetPath "OU=..."
```

**Organizational Units (OU) related**
```
1. List all OUs -> Get-ADOrganizationalUnit -Filter *
2. Create an OU -> New-ADOrganizationalUnit -Name "Sales" -Path "DC=corp,DC=local"
3. Get objects in an OU -> Get-ADObject -SearchBase "OU=Sales,DC=corp,DC=local" -Filter *
4. Remove an OU -> Remove-ADOrganizationalUnit -Identity "OU=Sales,DC=corp,DC=local"
5. Move an object into an OU -> Move-ADObject -Identity <DN> -TargetPath "OU=Sales,DC=corp,DC=local"
```

**Group Policy related**
```
1. List all GPOs -> Get-GPO -All
2. Get a specific GPO's info -> Get-GPO -Name "Default Domain Policy"
3. Create a new GPO -> New-GPO -Name "New Policy"
4. Link a GPO to an OU -> New-GPLink -Name "New Policy" -Target "OU=Sales,DC=corp,DC=local"
5. Generate GPO report (HTML) -> Get-GPOReport -Name "New Policy" -ReportType HTML -Path report.html
6. Force group policy update on a machine -> gpupdate /force
7. Show applied policy results -> gpresult /r
```

**Searching & Querying (legacy CLI tools)**
```
1. Query users -> dsquery user -name "john*"
2. Query computers -> dsquery computer -name "PC*"
3. Query groups -> dsquery group -name "IT*"
4. Get object details by DN -> dsget user "<DN>" -samid -display
5. General LDAP-style search -> dsquery * "DC=corp,DC=local" -filter "(objectClass=user)"
```

**Net commands (older but still common)**
```
1. Show domain info -> net accounts /domain
2. List domain users -> net user /domain
3. List domain groups -> net group /domain
4. Show group membership -> net group "IT-Team" /domain
5. Add a user to a domain group -> net group "IT-Team" jdoe /add /domain
6. Show current domain controller -> nltest /dsgetdc:corp.local
7. Test trust relationship -> nltest /sc_query:corp.local
```

**Replication & Domain Controller health**
```
1. Check replication status -> repadmin /replsummary
2. Force replication -> repadmin /syncall /AeD
3. Show replication partners -> repadmin /showrepl
4. Run domain health diagnostics -> dcdiag /v
5. Check FSMO role holders -> netdom query fsmo
6. Check DC time sync -> w32tm /query /status
```

**Trusts & Forest related**
```
1. List all forest trusts -> Get-ADTrust -Filter * | Select Name,Direction
2. Verify a trust -> netdom trust corp.local /domain:partner.local /verify
3. Get forest-wide info -> Get-ADForest | Select Domains,Sites,GlobalCatalogs
```

**Auditing & Security**
```
1. Find accounts with password never expires -> Get-ADUser -Filter * -Properties PasswordNeverExpires | Where PasswordNeverExpires -eq $true
2. Find inactive user accounts -> Search-ADAccount -AccountInactive -UsersOnly -TimeSpan 90.00:00:00
3. Find accounts with no password required -> Get-ADUser -Filter 'PasswordNotRequired -eq $true'
4. Check last logon time -> Get-ADUser jdoe -Properties LastLogonDate | Select LastLogonDate
5. Export all users to CSV for review -> Get-ADUser -Filter * -Properties * | Export-Csv users.csv
```

**Handy combos**
```
1. Get AD module loaded -> Import-Module ActiveDirectory
2. Quick user existence check -> Get-ADUser -Filter "SamAccountName -eq 'jdoe'"
3. Bulk disable inactive users -> Search-ADAccount -AccountInactive -TimeSpan 180.00:00:00 -UsersOnly | Disable-ADAccount
4. Export OU structure -> Get-ADOrganizationalUnit -Filter * | Select Name,DistinguishedName | Export-Csv ous.csv
5. Quick domain health check -> dcdiag /v | more
```
