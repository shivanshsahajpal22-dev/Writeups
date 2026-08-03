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
```
