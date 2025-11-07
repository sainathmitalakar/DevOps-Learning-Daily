**1. How do you troubleshoot when a Linux server becomes slow in production?**

- Check system resource usage using `top` or `htop` to identify which process consumes the most CPU or memory.  
- If it’s a memory issue, use `free -m` or `vmstat` to verify available memory and swap usage.  
- For disk issues, check space with `df -h` and I/O performance using `iostat`.  
- If CPU usage is high but not from user processes, inspect kernel-level interrupts using `mpstat -P ALL`.  
- Review system logs (`dmesg`, `/var/log/messages`) for any stuck processes or hardware errors.  
- Identify and restart any runaway services or processes causing performance issues.  


# 2. A deployment script failed because of a “Permission Denied” error — how do you handle it?

First, I check which user is running the script using whoami.
Then, I verify the file and directory permissions with ls -l to see if the user has the correct access rights.
If it’s a shell script, I ensure it has execute permission using chmod +x script.sh.
Sometimes the error comes from restricted directories like /etc or /var/log, so I may need to use sudo for admin privileges.
I also check the script for hardcoded paths or restricted commands.
Once fixed, I re-run it and confirm with logs that the issue is resolved.


