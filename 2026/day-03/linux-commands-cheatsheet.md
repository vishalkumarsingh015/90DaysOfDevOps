Linux Command Cheat Sheet
______________________________________________________________________________________________________________
Process Management – Linux Cheat Sheet
--------------------------------------------------------------------------------------------------------------
Manage system resources, view running tasks, and control process execution.

--------------------------------------------------------------------------------------------------------------
| Command   | Usage Example            | Descrip  
| --------- | ------------------------ | ------------------------------------------------------------------------------- |
| `ps`      | `ps aux`                 | Shows all running processes with details like user, PID, CPU, and memory usage. |
| `top`     | `top`                    | Displays real-time system processes and resource usage (CPU, RAM).              |
| `htop`    | `htop`                   | Interactive process viewer with a better UI than `top`.                         |
| `pgrep`   | `pgrep nginx`            | Finds the process ID (PID) of a running process by name.                        |
| `kill`    | `kill 1234`              | Gracefully stops a process using its PID.                                       |
| `kill -9` | `kill -9 1234`           | Forcefully terminates a process that is not responding.                         |
| `pkill`   | `pkill nginx`            | Kills processes based on their name instead of PID.                             |
| `nice`    | `nice -n 10 myscript.sh` | Starts a process with a specified priority level.                               |
| `renice`  | `renice -5 -p 1234`      | Changes the priority of a running process.                                      |
| `jobs`    | `jobs`                   | Lists background jobs in the current shell session.                             |
| `bg`      | `bg %1`                  | Resumes a stopped job in the background.                                        |
| `fg`      | `fg %1`                  | Brings a background job to the foreground.                                      |
| `nohup`   | `nohup python app.py &`  | Runs a command that continues even after the terminal is closed.                |
______________________________________________________________________________________________________________
File System Commands – Linux Cheat Sheet
--------------------------------------------------------------------------------------------------------------
Work with files, directories, permissions, and storage in the Linux file system.
-------------------------------------------------------------------------------------------------------------
| Command    | Usage Example                 | Description                                            |
| ---------- | ----------------------------- | ------------------------------------------------------ |
| `pwd`      | `pwd`                         | Displays the current working directory path.           |
| `ls`       | `ls -l`                       | Lists files and directories with detailed information. |
| `ls -a`    | `ls -a`                       | Shows all files including hidden files.                |
| `cd`       | `cd /home/user`               | Changes the current directory.                         |
| `mkdir`    | `mkdir project`               | Creates a new directory.                               |
| `mkdir -p` | `mkdir -p app/src/components` | Creates nested directories if they do not exist.       |
| `touch`    | `touch file.txt`              | Creates a new empty file.                              |
| `cp`       | `cp file1.txt backup.txt`     | Copies a file from one location to another.            |
| `cp -r`    | `cp -r folder1 folder2`       | Copies directories recursively.                        |
| `mv`       | `mv old.txt new.txt`          | Moves or renames a file or directory.                  |
| `rm`       | `rm file.txt`                 | Deletes a file.                                        |
| `rm -r`    | `rm -r folder`                | Removes a directory and its contents.                  |
| `cat`      | `cat notes.txt`               | Displays the contents of a file.                       |
| `less`     | `less largefile.log`          | Views file content page by page.                       |
| `head`     | `head file.txt`               | Shows the first 10 lines of a file.                    |
| `tail`     | `tail file.txt`               | Shows the last 10 lines of a file.                     |
| `tail -f`  | `tail -f app.log`             | Monitors a file in real time (commonly used for logs). |
| `find`     | `find /home -name file.txt`   | Searches for files or directories.                     |
| `grep`     | `grep "error" logfile.log`    | Searches for a specific text pattern inside files.     |
| `chmod`    | `chmod 755 script.sh`         | Changes file permissions.                              |
| `chown`    | `chown user:user file.txt`    | Changes file ownership.                                |
| `df -h`    | `df -h`                       | Shows disk space usage in human-readable format.       |
| `du -sh`   | `du -sh folder`               | Displays the size of a directory.                      |

____________________________________________________________________________________________________________
Networking Troubleshooting Commands – Linux Cheat Sheet
------------------------------------------------------------------------------------------------------------
Diagnose connectivity issues, inspect network configuration, and test services.
-----------------------------------------------------------------------------------------------------------
| Command       | Usage Example                       | Description                                                            |
| ------------- | ----------------------------------- | ---------------------------------------------------------------------- |
| `ip`          | `ip a`                              | Displays IP addresses and network interfaces on the system.            |
| `hostname`    | `hostname -I`                       | Shows the system’s IP address.                                         |
| `ping`        | `ping google.com`                   | Tests connectivity to another host and checks network latency.         |
| `traceroute`  | `traceroute google.com`             | Shows the path packets take to reach a destination.                    |
| `tracepath`   | `tracepath google.com`              | Similar to traceroute; shows network path without needing root access. |
| `nslookup`    | `nslookup google.com`               | Queries DNS servers to resolve domain names.                           |
| `dig`         | `dig google.com`                    | Provides detailed DNS query results for troubleshooting.               |
| `host`        | `host google.com`                   | Performs DNS lookup to find IP addresses for a domain.                 |
| `ss`          | `ss -tuln`                          | Displays listening ports and active network connections.               |
| `netstat`     | `netstat -tuln`                     | Shows open ports, active connections, and network statistics.          |
| `lsof`        | `lsof -i :80`                       | Lists processes using a specific network port.                         |
| `curl`        | `curl -I https://google.com`        | Tests HTTP/HTTPS connectivity and retrieves response headers.          |
| `wget`        | `wget https://example.com/file.zip` | Downloads files from the internet via HTTP/HTTPS.                      |
| `nc` (Netcat) | `nc -zv google.com 80`              | Tests if a remote port is open and reachable.                          |
| `telnet`      | `telnet google.com 80`              | Tests connectivity to a specific port on a remote host.                |
| `route`       | `route -n`                          | Displays the system routing table.                                     |
| `ip route`    | `ip route`                          | Shows routing information and default gateway.                         |


