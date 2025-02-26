# Lab 3: Create a shell script  
## Create a shell script to ping every server in the 172.16.17.x subnet (where x is a number between 0 and 255). If the ping succeeds, display the message “Server 172.16.17.x is up and running” If the ping fails, display the message “Server 172.16.17.x is unreachable”.

## Steps to Use the Script:
### 1- Create the Script File: Save the script to a file :
```
vim ping_servers.sh
```
### Script
```
#!/bin/bash

// Iterate through all possible IP addresses in the 172.16.17.x subnet
for i in {0..255}; do
  // Define the current IP address
  ip="172.16.17.$i"
  
  
  ping  -c 1 $ip
  
  // Check the exit status of the ping command
  if [ $? -eq 0 ]; then
    echo "Server $ip is up and running"
  else
    echo "Server $ip is unreachable"
  fi
done
```
### 2- Make the Script Executable: Run the following to make the script executable:
```
chmod +x ping_servers.sh
```
### 3- Run the Script: Execute the script:
```
./ping_servers.sh
```
## Explanation of the Script:
- for x in {0..255}: Loops through numbers from 0 to 255.
- ping -c 1 : Sends one ping request to the target IP .
- if condition checks the result of the ping command:
- If successful, it prints "Server ... is up and running."
- If unsuccessful, it prints "Server ... is unreachable."
## Output Example:
```
Server 172.16.17.220 is unreachable
PING 172.16.17.221 (172.16.17.221) 56(84) bytes of data.

172.16.17.221 ping statistics
1 packets transmitted, 0 received, 100% packet loss, time Oms

Server 172.16.17.221 is unreachable
PING 172.16.17.222 (172.16.17.222) 56(84) bytes of data.

172.16.17.222 ping statistics
1 packets transmitted, 0 received, 100% packet loss, time Oms

Server 172.16.17.222 is unreachable
PING 172.16.17.223 (172.16.17.223) 56(84) bytes of data.

172.16.17.223 ping statistics
1 packets transmitted, 0 received, 100% packet loss, time Oms

Server 172.16.17.223 is unreachable
PING 172.16.17.224 (172.16.17.224) 56(84) bytes of data.
...
```
This script will check all IPs in the 172.16.17.x subnet and display their status.

