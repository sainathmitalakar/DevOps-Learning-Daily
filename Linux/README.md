**1. How do you troubleshoot when a Linux server becomes slow in production?**

- Start by checking real-time system performance using `top` or `htop` to identify which process is consuming high CPU or   memory.  
- If memory usage seems high, use `free -m` or `vmstat` to verify available memory and swap usage.  
- For disk-related issues, check disk space with `df -h` and monitor disk I/O using `iostat`.  
- When CPU usage is high but not from user processes, use `mpstat -P ALL` to inspect CPU utilization per core.  
- Review system logs with `dmesg` and `/var/log/messages` to detect hardware errors or kernel-related issues.  
- Check for zombie or stuck processes using `ps -ef | grep defunct`.  
- If a specific service is the cause, restart it safely using `systemctl restart <service-name>`.  
- Finally, if issues persist, analyze load averages with `uptime` to determine long-term performance trends.  

**Commands used in this scenario:** top
htop
free -m
vmstat
df -h
iostat
mpstat -P ALL
dmesg
cat /var/log/messages
ps -ef | grep defunct
systemctl restart <service-name>
uptime

# 2. A deployment script failed because of a “Permission Denied” error — how do you handle it?

First, I check which user is running the script using whoami.
Then, I verify the file and directory permissions with ls -l to see if the user has the correct access rights.
If it’s a shell script, I ensure it has execute permission using chmod +x script.sh.
Sometimes the error comes from restricted directories like /etc or /var/log, so I may need to use sudo for admin privileges.
I also check the script for hardcoded paths or restricted commands.
Once fixed, I re-run it and confirm with logs that the issue is resolved.



