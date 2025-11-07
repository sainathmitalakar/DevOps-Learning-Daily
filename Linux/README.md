1. How do you troubleshoot when a Linux server becomes slow in production?

First, I check the system resource usage using top or htop to see which process is consuming the most CPU or memory.
If it’s a memory issue, I use free -m or vmstat to verify available memory and swap usage.
For disk issues, I check space with df -h and I/O performance using iostat.
If the CPU usage is high but not from user processes, I check kernel-level interrupts using mpstat -P ALL and look for any stuck processes in dmesg or /var/log/messages.
Finally, I might check for runaway services or memory leaks and restart the affected service if required.
