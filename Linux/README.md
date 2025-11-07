**1. How do you troubleshoot when a Linux server becomes slow in production?**

- Start by checking real-time system performance to identify high CPU or memory usage.  
- If memory usage is high, verify available memory and swap.  
- For disk-related issues, check disk space and I/O performance.  
- Inspect CPU usage per core if CPU is high but not from user processes.  
- Review system logs to detect hardware errors or kernel-related issues.  
- Check for zombie or stuck processes.  
- Restart any specific service safely if needed.  
- Analyze load averages for long-term performance trends.  

**Commands used in this scenario:**

```bash
top
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




