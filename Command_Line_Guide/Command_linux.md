# Most used Linux commands 

**Movement-related**
```
1. Current directory -> pwd
2. List all files -> ls -la
3. Change directory -> cd
4. Go to previous directory -> cd ..
5. Go to last directory -> cd -
6. Go to home directory -> cd ~
7. Show directory as tree -> ls -r, tree 
```

**File-related**
```
1. Create files -> touch file.txt
2. Make directories -> mkdir -p
3. Copy a file -> cp file /path
4. Copy recursively -> cp -r dir dest
5. Move/rename -> mv old new
6. Remove a file -> rm file
7. Remove a dir -> rm -rf dir
8. Finding a file -> find <dir> -name <name>
9. Files modified in a certain time period -> find <dir> -mtime -<time in day>
10. Fast file search -> fast file search
```

**Viewing and editing**
```
1. Print whole file -> cat file
2. Scroll through file -> less file
3. First 20 lines -> head -n 20 file
4. Last 20 lines -> tail -n 20 file
5. Follow live file -> tail -f file
6. Simple editor -> nano file
7. Powerful editor -> vim file
8. Count lines -> wc -l file 
```
**Searching inside files**
```
1. Search text in file -> grep "pattern" file
2. Search recursively -> grep -r "pattern" dir/
3. Search case-insensitive -> grep -i "pattern" file
4. Search with line number -> grep -n "pattern" file
5. search invert match -> grep -v "pattern" file 
```

**premission & Ownership**
```
1. changing permission -> chmod <permssion number> file
2. Making executable -> chmod +x script.sh
3. Change owner/group -> change owner/group
4. Running command with sudo -> sudo command 
```

**Process management**
```
1. List all running processes -> ps aux 
2. Live process viewer -> top
3. Nicer live process viewer  -> Htop
4. Terminate a process -> kill PID
5. Force kill something -> kill -9 PID
6. Kill all processes by name -> kilall name
7. List background jobs -> jobs
8. Backgound/Foreground -> fg / bg
9. Run immune to hangups -> nohup cmd &
10. Detach from shell -> disown 
```

**System info**
```
1. Disk space -> df -h
2. Size of a directory -> du -sh dir/
3. Size of items in current dir -> du -sh * | sort -h
4. Memory usage -> free -h
5. Kernel/system info -> uname -a
6. Uptime -> uptime
7. CPU info -> lscpu
8. List block devices/partitions -> lsblk 
```

**Networking**
```
1. Testing connectivity -> ping host
2. Fetch URL -> curl url
3. Fetch header only -> curl -I url
4. Download a file -> wget url
5. Remote login -> ssh host@ip
6. Copy file over SSH -> scp file user@host:/path
7. Efficient syn/copy (local or remote) -> rsync -avz src/ dest/
8. Show network interfaces -> ip a
9. Show network interfaces -> ipconfig
10. Show listening ports ->  netstat -tulpn
11. Show listening ports (modern) -> ss -tulpn
12. DNS lookup -> dig domain / nslookup domain 
```

**Archive & compression**
```
1. compress directory into .tar.gz -> tar -czvf out.tar.gz dir/   
2. extract .tar.gz -> tar -xzvf file.tar.gz 
3. Zip a directory -> zip -r out.zip dir/
4. Unzip a directory -> unzip file.zip
```

**Package management**
```
 Debian/Ubuntu
sudo apt update && sudo apt upgrade
sudo apt install package
sudo apt remove package

# Fedora/RHEL
sudo dnf install package

# Arch
sudo pacman -S package
```

**Redirection and pipes**
```
1. Overwrite file with output -> cmd > file
2. Append output to a file -> cmd >> file
3. Use file as input -> cmd < file
4. Piping one command into another -> cmd 1 | cmd 2
5. Redirect errors only -> cmd 2> errors.log
6. Redirect both stdout and stderr -> cmd > out.log 2>&1                   
```

**Environment and shell**
```
1. echo $var ->  print variables
2. Set variables equal to something -> export VAR=value
3. Show the path of a command -> which command
4. Create a shortcut -> alias ll="ls -la"
5. Show command history -> history
6. Return command 123 from history -> !123
7. Reload shell config -> source ~/.bashrc
8. List env variables -> env
```
**User and system management**
```
1. Current user -> whoami
2. User/Group UID -> id
3. Add a user (Debian family) -> adduser username  
4. Change password -> passwd username 
5. Switch username -> switch user 
6. Last command with sudo -> sudo !!
```
**Text processing**
```      
1. Print first column -> awk '{print $1}' file
2. Find and replace -> sed 's/old/new/g' file
3. Sort files -> sort file
4. Sort and remove duplicates -> sort -u file
5. Remove adjacent duplicate lines -> uniq
6. Extract column 2 from CSV -> cut -d, -f2 file
7. Build and run commands from input -> xargs
8. Translate characters -> tr 'a-z' 'A-Z' < file 
```
**System services**
```
1. Check service status -> systemctl status service
2. Start a system service -> sudo systemctl start service
3. Stop a system service ->  sudo systemctl stop service
4. Restart a system service -> sudo systemctl restart service
5. Start a service on boot -> sudo systemctl enable service
6. View service logs -> journalctl -u service
7. View live system logs -> journalctl -f      
```
**Handy command combos**
```
1. Kill a running command -> Ctrl+C
2. Suspend a running command -> Crtl+Z
3. Search command history -> Ctrl+R
4. Repeat last command -> !!
5. Manual page -> man command
6. Quick usage help -> command --help
7. Rerun a command in a certain interval -> watch -n 2 command
8. Quick health check -> df -h && free -h  
```
