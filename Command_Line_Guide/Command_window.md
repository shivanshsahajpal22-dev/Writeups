# Most used Windows commands
(Both command line and powershell)

**Movement-related**
```
1. Current directory -> cd  (or Get-Location in PowerShell)
2. List all files -> dir /a  (or Get-ChildItem -Force in PowerShell)
3. Change directory -> cd
4. Go to previous directory -> cd ..
5. Go to last directory -> pushd - / popd  (PowerShell: cd -)
6. Go to home directory -> cd %USERPROFILE%  (PowerShell: cd ~)
7. Show directory as tree -> tree /f
```

**File-related**
```
1. Create files -> type nul > file.txt  (PowerShell: New-Item file.txt)
2. Make directories -> mkdir dir\sub\sub2  (PowerShell: New-Item -ItemType Directory -Force)
3. Copy a file -> copy file dest  (PowerShell: Copy-Item)
4. Copy recursively -> xcopy dir dest /E /I  (PowerShell: Copy-Item -Recurse)
5. Move/rename -> move old new  (PowerShell: Move-Item / Rename-Item)
6. Remove a file -> del file  (PowerShell: Remove-Item)
7. Remove a dir -> rmdir /s /q dir  (PowerShell: Remove-Item -Recurse -Force)
8. Finding a file -> dir /s /b <name>  (PowerShell: Get-ChildItem -Recurse -Filter <name>)
9. Files modified in a certain time period -> forfiles /p <dir> /d -7 /s  (PowerShell: Get-ChildItem -Recurse | Where LastWriteTime -gt (Get-Date).AddDays(-7))
10. Fast file search -> Windows Search / Everything (third-party tool)
```

**Viewing and editing**
```
1. Print whole file -> type file  (PowerShell: Get-Content file)
2. Scroll through file -> more file  (PowerShell: Get-Content file | more)
3. First 20 lines -> PowerShell: Get-Content file -TotalCount 20
4. Last 20 lines -> PowerShell: Get-Content file -Tail 20
5. Follow live file -> PowerShell: Get-Content file -Wait -Tail 10
6. Simple editor -> notepad file
7. Powerful editor -> code file  (VS Code) or notepad++ file
8. Count lines -> find /c /v "" file  (PowerShell: (Get-Content file).Count)
```

**Searching inside files**
```
1. Search text in file -> findstr "pattern" file  (PowerShell: Select-String "pattern" file)
2. Search recursively -> findstr /s "pattern" *.*  (PowerShell: Select-String "pattern" -Path dir\* -Recurse)
3. Search case-insensitive -> findstr /i "pattern" file  (PowerShell: Select-String -CaseSensitive:$false)
4. Search with line number -> findstr /n "pattern" file  (Select-String shows line numbers by default)
5. Search invert match -> findstr /v "pattern" file  (PowerShell: Select-String -NotMatch)
```

**Permission & Ownership**
```
1. Changing permission -> icacls file /grant user:F  (sets full control)
2. Making executable -> not needed; Windows uses file extensions (.exe, .bat, .ps1) instead of exec bit
3. Change owner/group -> takeown /f file  (PowerShell: Set-Acl / icacls)
4. Running command with elevated rights -> Run as Administrator  (PowerShell: Start-Process -Verb RunAs)
```

**Process management**
```
1. List all running processes -> tasklist  (PowerShell: Get-Process)
2. Live process viewer -> Task Manager (taskmgr)  (PowerShell: Get-Process | Sort CPU -Descending)
3. Nicer live process viewer -> Process Explorer (Sysinternals)
4. Terminate a process -> taskkill /PID <pid>  (PowerShell: Stop-Process -Id <pid>)
5. Force kill something -> taskkill /F /PID <pid>  (PowerShell: Stop-Process -Id <pid> -Force)
6. Kill all processes by name -> taskkill /F /IM name.exe  (PowerShell: Stop-Process -Name name -Force)
7. List background jobs -> PowerShell: Get-Job
8. Background/Foreground -> PowerShell: Start-Job / Receive-Job (no direct bg/fg like bash)
9. Run immune to hangups -> start /B cmd  (PowerShell: Start-Process -WindowStyle Hidden)
10. Detach from shell -> PowerShell: Start-Process (runs detached by default)
```

**System info**
```
1. Disk space -> wmic logicaldisk get size,freespace,caption  (PowerShell: Get-PSDrive)
2. Size of a directory -> PowerShell: (Get-ChildItem dir -Recurse | Measure-Object Length -Sum).Sum
3. Size of items in current dir -> PowerShell: Get-ChildItem | Select Name, Length | Sort Length -Descending
4. Memory usage -> systeminfo | findstr Memory  (PowerShell: Get-CimInstance Win32_OperatingSystem)
5. Kernel/system info -> systeminfo
6. Uptime -> net statistics workstation  (PowerShell: (Get-CimInstance Win32_OperatingSystem).LastBootUpTime)
7. CPU info -> wmic cpu get name  (PowerShell: Get-CimInstance Win32_Processor)
8. List block devices/partitions -> wmic diskdrive list brief  (PowerShell: Get-Disk / Get-Partition)
```

**Networking**
```
1. Testing connectivity -> ping host
2. Fetch URL -> curl url  (built into modern Windows; PowerShell: Invoke-WebRequest url)
3. Fetch header only -> curl -I url  (PowerShell: (Invoke-WebRequest url).Headers)
4. Download a file -> curl -O url  (PowerShell: Invoke-WebRequest url -OutFile file)
5. Remote login -> ssh host@ip  (OpenSSH client built into Windows 10+)
6. Copy file over SSH -> scp file user@host:/path
7. Efficient sync/copy (local or remote) -> robocopy src dest /E  (rsync via WSL for remote sync)
8. Show network interfaces -> ipconfig /all  (PowerShell: Get-NetIPConfiguration)
9. Show network interfaces (legacy alt) -> ipconfig
10. Show listening ports -> netstat -ano
11. Show listening ports (modern) -> PowerShell: Get-NetTCPConnection
12. DNS lookup -> nslookup domain  (PowerShell: Resolve-DnsName domain)
```

**Archive & compression**
```
1. Compress directory into .zip -> PowerShell: Compress-Archive -Path dir -DestinationPath out.zip
2. Extract .zip -> PowerShell: Expand-Archive file.zip -DestinationPath dest
3. Zip a directory (alt) -> tar -czvf out.tar.gz dir  (tar is built into modern Windows too)
4. Unzip a directory (alt) -> tar -xzvf file.tar.gz
```

**Package management**
```
# Windows (winget - built into Windows 10/11)
winget upgrade --all
winget install package
winget uninstall package

# Chocolatey
choco upgrade all
choco install package
choco uninstall package

# Scoop
scoop update *
scoop install package
scoop uninstall package
```

**Redirection and pipes**
```
1. Overwrite file with output -> cmd > file
2. Append output to a file -> cmd >> file
3. Use file as input -> cmd < file
4. Piping one command into another -> cmd1 | cmd2
5. Redirect errors only -> cmd 2> errors.log
6. Redirect both stdout and stderr -> cmd > out.log 2>&1
```

**Environment and shell**
```
1. echo %VAR% -> print variables  (PowerShell: echo $env:VAR)
2. Set variables equal to something -> set VAR=value  (PowerShell: $env:VAR = "value")
3. Show the path of a command -> where command  (PowerShell: Get-Command command)
4. Create a shortcut -> doskey ll=dir /a $*  (PowerShell: Set-Alias / function in profile)
5. Show command history -> doskey /history  (PowerShell: Get-History)
6. Return command 123 from history -> PowerShell: Invoke-History 123
7. Reload shell config -> PowerShell: . $PROFILE
8. List env variables -> set  (PowerShell: Get-ChildItem Env:)
```

**User and system management**
```
1. Current user -> whoami
2. User/Group SID -> whoami /user
3. Add a user -> net user username /add
4. Change password -> net user username *
5. Switch user -> runas /user:username cmd
6. Last command with elevated rights -> re-run in an Administrator shell (no direct sudo !! equivalent)
```

**Text processing**
```
1. Print first column -> PowerShell: Get-Content file | ForEach {($_ -split '\s+')[0]}
2. Find and replace -> PowerShell: (Get-Content file) -replace 'old','new' | Set-Content file
3. Sort files -> sort file  (PowerShell: Get-Content file | Sort-Object)
4. Sort and remove duplicates -> PowerShell: Get-Content file | Sort-Object -Unique
5. Remove adjacent duplicate lines -> PowerShell: Get-Content file | Get-Unique
6. Extract column 2 from CSV -> PowerShell: Import-Csv file | Select-Object -ExpandProperty Column2
7. Build and run commands from input -> PowerShell: ForEach-Object { }  (no direct xargs, but pipeline does this)
8. Translate characters -> PowerShell: (Get-Content file) -replace 'a','A' -replace 'b','B' ...
```

**System services**
```
1. Check service status -> sc query service  (PowerShell: Get-Service service)
2. Start a system service -> sc start service  (PowerShell: Start-Service service)
3. Stop a system service -> sc stop service  (PowerShell: Stop-Service service)
4. Restart a system service -> PowerShell: Restart-Service service
5. Start a service on boot -> sc config service start=auto  (PowerShell: Set-Service -StartupType Automatic)
6. View service logs -> Event Viewer  (PowerShell: Get-EventLog / Get-WinEvent)
7. View live system logs -> PowerShell: Get-WinEvent -LogName System -MaxEvents 20 (no direct "follow" mode)
```

**Handy command combos**
```
1. Kill a running command -> Ctrl+C
2. Suspend a running command -> not natively supported (no Ctrl+Z job control in cmd/PowerShell)
3. Search command history -> F8 (cmd) / Ctrl+R (PowerShell with PSReadLine)
4. Repeat last command -> F3 (cmd)  (PowerShell: Invoke-History or up-arrow)
5. Manual page -> help command  (PowerShell: Get-Help command -Full)
6. Quick usage help -> command /?  (PowerShell: Get-Help command)
7. Rerun a command in a certain interval -> PowerShell: while($true){command; Start-Sleep 2}
8. Quick health check -> systeminfo | findstr /C:"Total Physical Memory"
```

