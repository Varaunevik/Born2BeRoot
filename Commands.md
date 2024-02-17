# Commands

- `sudo ufw status`  to checks whether firewall is active
- `sudo systemctl status ssh`  checks whether ssh connection is active
- `getent group sudo`  check which users are found within the group
- `getent group user42`  check which users are found within the group
- `sudo adduser new username`  add new user
- `sudo groupadd groupname`  add new group (you will be prompted for a password as well)
- `sudo usermod -aG groupname username` add user to group (a = append, which makes the user not be removed from the other groups mention
- `sudo chage -l username` - check password expire rules
- `sudo gpasswd -d username groupname` remove user from group
- `hostnamectl`
- `hostnamectl set-hostname new_hostname` - to change the current hlsbostname
- sudo reboot Restart your Virtual Machine.
- `sudo nano /etc/hosts` - change current hostname to new hostname
- `lsblk` to display the partitions
- `dpkg -l | grep sudo –` to show that sudo is installed
- `sudo ufw status numbered`
- `sudo ufw allow port-id`
- `sudo ufw delete rule number`
- `ssh your_user_id@127.0.0.1 -p 4242` - do this in terminal to show that SSH to port 4242 is working
- `cd /usr/local/bin` – to show monitoring.sh
- `sudo crontab -u root -e` – to edit the cron job
- `change script to */1 * * * * sleep 30s && script path` – to run it every 30 seconds, delete the line to stop the job from running.

**CHAGE:**

```
Syntax: chage [options] USERNAME

```

```
-d LAST_DAY Indicates the day the password was last changed
-E EXPIRE_DATE Sets the account expiration date
-I INACTIVE Changes the password in an inactive state after the account expires
-l Shows account aging information
-m MIN_DAYS Sets the minimum number of days between password changes
-M MAX_DAYS Sets the maximum number of days a password is valid
-W WARN_DAYS Sets the number of days to warn before the password expires
```
