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
```bash

  **2. A deployment script failed because of a “Permission Denied” error — how do you handle it?**

- Check which user is running the script.  
- Verify file and directory permissions to ensure the user has proper access.  
- Make sure the script has execute permission if it’s a shell script.  
- Use `sudo` if the script requires admin privileges for restricted directories.  
- Inspect the script for hardcoded paths or commands that require elevated access.  
- Re-run the script after changes and verify logs to confirm the issue is fixed.  

**Commands used in this scenario:**

```bash
whoami
ls -l
chmod +x script.sh
sudo ./script.sh
cat /var/log/<relevant-log-file>





