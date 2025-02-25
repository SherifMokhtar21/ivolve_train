# Lab 1: Create a new group named ivolve and a new user assigned to this group with a secure password. Configure the user’s permissions to allow installing Nginx with elevated privileges using the sudo tool (run sudo command for installing nginx without password). 
In this lab, you will:

1-Create a user named (your name ) in this case -> ("sherif") 😊.
2-Create a group named ivolve.
3-Add the ("sherif") user to the ivolve group.
4-Configure the ("sherif") user to install and manage Nginx without being prompted for a sudo password
## Steps
### 1. Create the ivolve group 
```
sudo groupadd ivolve
```
### 2. 2. Create the sherif user with password
```
sudo adduser sherif
sudo passwd sherif

```
### 3. Add sherif to the ivolve group
```
sudo usermod -aG ivolve sherif
```
### 4. Modify sudoers file to allow passwordless Nginx installation
```
sudo visudo
sherif ALL=(ALL) NOPASSWD: /bin/yum install -y nginx
```
### 5. Add the Nginx Repository Manually 
```
sudo nano /etc/yum.repos.d/nginx.repo

```
### 6. Add the following content
```
[nginx]
name=Nginx Repository
baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
gpgcheck=0
enabled=1

```
### 6. Install nginx 
```
sudo -i -u sherif
sudo yum install -y nginx

```

