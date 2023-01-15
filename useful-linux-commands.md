# Linux Useful Commands

## Commands

- Backup from server to ftp server

  ```bash
  FTP_PASSWORD=YOUR_PASS duplicity /PATH_TO_DIR ftp://USER_NAME@domain.com/PATH
  ```

- Show all folder size in the current directory

  ```bash
  du -h --max-depth=1
  ```

#### User commands

- List of all users

  ```bash
  # with details
  cat /etc/passwd

  # just user name
  awk -F':' '{ print $1}' /etc/passwd
  # Or
  cut -d: -f1 /etc/passwd
  ```

- Get a list of all users using the getent command

  ```bash
  getent passwd
  getent passwd | grep tom
  ## get a list all users ##
  getent passwd | cut -d: -f1
  ## count all user accounts using the wc ##
  getent passwd | wc -l
  ```

Script for get lists both system and users accounts, [here](https://github.com/ehsanghaffar/learning-bash-scripting/blob/main/part01/users_list.sh)

- SSL Cert for domain

apt install socat -y
wget -O - <https://get.acme.sh> | sh
source ~/.bashrc
acme.sh --upgrade --auto-upgrade
acme.sh --register-account -m arspand@gmail.com
acme.sh --issue -d serve1.eindev.tk --standalone

- Change tcp connections limit
  ```bash
  nano /etc/sysctl.conf
  #add for c10k
  net.core.somaxconn = 65536
  net.ipv4.tcp_max_tw_buckets = 1440000
  fs.file-max = 2097152

  nano /etc/security/limits.conf
  #add for c10k
  * hard nofile 65535
  * soft nofile 65535
  * hard nproc 65535
  * soft nproc 65535

  nano /etc/pam.d/common-session
  #c10k (optional)
  session required pam_limits.so
  ```