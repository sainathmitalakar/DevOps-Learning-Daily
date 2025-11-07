1. How do you troubleshoot when a Linux server becomes slow in production?

First, I check the system resource usage using top or htop to see which process is consuming the most CPU or memory.
If it’s a memory issue, I use free -m or vmstat to verify available memory and swap usage.
For disk issues, I check space with df -h and I/O performance using iostat.
If the CPU usage is high but not from user processes, I check kernel-level interrupts using mpstat -P ALL and look for any stuck processes in dmesg or /var/log/messages.
Finally, I might check for runaway services or memory leaks and restart the affected service if required.

2. A deployment script failed because of a “Permission Denied” error — how do you handle it?

First, I check which user is running the script using whoami.
Then, I verify the file and directory permissions with ls -l to see if the user has the correct access rights.
If it’s a shell script, I ensure it has execute permission using chmod +x script.sh.
Sometimes the error comes from restricted directories like /etc or /var/log, so I may need to use sudo for admin privileges.
I also check the script for hardcoded paths or restricted commands.
Once fixed, I re-run it and confirm with logs that the issue is resolved.
