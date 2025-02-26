# Lab 5: Generate public and private keys and enable SSH from your machine to another VM using the key. Configure SSH to just run ‘ssh ivolve’  without specify username, IP and key in the command.
## Overview: SSH Key Authentication with Alias Configuration
This lab demonstrates how to set up SSH key-based authentication between your machine and another VM, eliminating the need to specify the username, IP address, and key manually. You will configure an SSH alias named ivolve for easy access.
## Step-by-Step Guide
### Step 1: Generate SSH Keys
#### 1- Generate an SSH key pair:
```
ssh-keygen -t rsa -b 2048 -f ~/.ssh/ivolve_key
```
#### 2- Confirm the key files:
- Private key: ~/.ssh/ivolve_key
- Public key: ~/.ssh/ivolve_key.pub
### Step 2: Copy the Public Key to the VM
#### 1- Use the ssh-copy-id command to copy the public key to the remote VM:
```
ssh-copy-id -i ~/.ssh/ivolve_key.pub student@192.168.24.132
```
#### 2- Verify that key-based authentication works:
```
ssh -i ~/.ssh/ivolve_key username@192.168.24.132
```
### Step 3: Configure the SSH Alias
#### 1- Open the SSH configuration file:
```
nano ~/.ssh/config
```
#### 2- Add the following configuration:
```
Host ivolve
    HostName 192.168.24.132
    User student
    IdentityFile ~/.ssh/ivolve_key
```
#### 3- Save and exit the file.

### Step 4:Test the SSH Alias
#### 1- Test the alias by running:
```
ssh ivolve
```
#### 2- You should be able to log in without specifying the username, IP address, or key.
# Outcome
-Activate the web console with: systemctl enable --now cockpit.socket

-Register this system with Red Hat Insights: insights-client --register
-Create an account or view all your systems at https://red.ht/insights-dashboard
-Last login: Tue Feb 25 11:29:08 2025 from 192.168.24.132



