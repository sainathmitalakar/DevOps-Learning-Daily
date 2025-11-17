# Linux for DevOps — Daily Scenarios

Welcome to the **Linux DevOps Learning Hub**.  
All scenarios are structured like a web page with collapsible answers and command blocks.  

---

<details>
<summary><b>1. How do you troubleshoot when a Linux server becomes slow in production?</b></summary>

### Steps:
<ul>
<li>Start by checking real-time system performance to identify high CPU or memory usage.</li>
<li>If memory usage is high, verify available memory and swap.</li>
<li>For disk-related issues, check disk space and I/O performance.</li>
<li>Inspect CPU usage per core if CPU is high but not from user processes.</li>
<li>Review system logs to detect hardware errors or kernel-related issues.</li>
<li>Check for zombie or stuck processes.</li>
<li>Restart any specific service safely if needed.</li>
<li>Analyze load averages for long-term performance trends.</li>
</ul>

### Commands used in this scenario:

<pre>
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
systemctl restart &lt;service-name&gt;
uptime
</pre>

</details>

---

<details>
<summary><b>2. A deployment script failed because of a “Permission Denied” error — how do you handle it?</b></summary>

### Steps:
<ul>
<li>Check which user is running the script.</li>
<li>Verify file and directory permissions to ensure the user has proper access.</li>
<li>Make sure the script has execute permission if it’s a shell script.</li>
<li>Use <code>sudo</code> if the script requires admin privileges for restricted directories.</li>
<li>Inspect the script for hardcoded paths or commands that require elevated access.</li>
<li>Re-run the script after changes and verify logs to confirm the issue is fixed.</li>
</ul>

### Commands used in this scenario:

<pre>
whoami
ls -l
chmod +x script.sh
sudo ./script.sh
cat /var/log/&lt;relevant-log-file&gt;
</pre>

</details>

---


<details>
<summary><b>3. How do you check why a Linux service failed to start?</b></summary>

### Steps:
<ul>
<li>Check the service status using <code>systemctl status</code>.</li>
<li>Review journal logs for errors: <code>journalctl -xe</code>.</li>
<li>Look for missing dependencies or misconfigurations.</li>
<li>Try starting the service manually and observe any errors.</li>
<li>Verify file permissions and ownership if the service accesses files.</li>
</ul>

### Commands used in this scenario:

<pre>
systemctl status &lt;service-name&gt;
journalctl -xe
systemctl start &lt;service-name&gt;
ls -l /path/to/service/files
</pre>

</details>

---
<details>
<summary><b>4. How do you find and kill a runaway process consuming high CPU?</b></summary>

### Steps:
<ul>
<li>Use <code>top</code> or <code>htop</code> to identify processes consuming high CPU.</li>
<li>Note the process ID (PID).</li>
<li>Kill the process gracefully with <code>kill PID</code>.</li>
<li>If it doesn’t stop, force kill with <code>kill -9 PID</code>.</li>
<li>Check logs to understand why the process spiked.</li>
</ul>

### Commands used in this scenario:

<pre>
top
htop
ps -aux --sort=-%cpu | head -n 10
kill &lt;PID&gt;
kill -9 &lt;PID&gt;
cat /var/log/&lt;application-log&gt;
</pre>

</details>

---

<details>
<summary><b>5. How do you monitor disk usage and prevent full disk issues in production?</b></summary>

### Steps:
<ul>
<li>Check disk usage with <code>df -h</code>.</li>
<li>Analyze directory size with <code>du -sh /path/*</code>.</li>
<li>Set up alerts for disk usage thresholds.</li>
<li>Clean old logs and temporary files regularly.</li>
<li>Consider moving large data to separate partitions or external storage.</li>
</ul>

### Commands used in this scenario:

<pre>
df -h
du -sh /path/*
find /var/log -type f -name "*.log" -mtime +30 -exec rm -f {} \;
ncdu / (optional interactive disk analyzer)
</pre>

</details>

---

<details>
<summary><b>6. How do you check network connectivity issues on a Linux server?</b></summary>

### Steps:
<ul>
<li>Ping the remote host to verify connectivity.</li>
<li>Check routing tables and network interfaces.</li>
<li>Inspect firewall rules for blocked traffic.</li>
<li>Use <code>traceroute</code> to identify network hops and latency.</li>
<li>Check DNS resolution if hostname cannot be reached.</li>
</ul>

### Commands used in this scenario:

<pre>
ping &lt;host&gt;
ip addr
ip route
iptables -L -n
traceroute &lt;host&gt;
nslookup &lt;hostname&gt;
</pre>

</details>

---
<details>
<summary><b>7. How do you handle a full memory (RAM) situation causing application crashes?</b></summary>

### Steps:
<ul>
<li>Check current memory usage with <code>free -m</code> or <code>vmstat</code>.</li>
<li>Identify memory-hungry processes using <code>top</code> or <code>htop</code>.</li>
<li>Consider restarting or tuning the configuration of memory-intensive services.</li>
<li>Check for memory leaks in custom applications or scripts.</li>
<li>Enable or adjust swap space to prevent immediate crashes.</li>
<li>Plan for scaling or optimizing applications to reduce memory footprint.</li>
</ul>

### Commands used in this scenario:

<pre>
free -m
vmstat 5
top
htop
ps aux --sort=-%mem | head -n 10
swapon -s
sudo swapoff -a && sudo swapon -a
</pre>

</details>

---

<details>
<summary><b>8. How do you safely update packages and the Linux kernel in production?</b></summary>

### Steps:
<ul>
<li>Check current system version and kernel version.</li>
<li>Update package repositories before upgrading.</li>
<li>Review changelogs for critical services or dependencies.</li>
<li>Apply updates in a staged manner (test server first if possible).</li>
<li>Reboot only if required by kernel updates and ensure service availability.</li>
<li>Verify the system and services after updates to confirm stability.</li>
</ul>

### Commands used in this scenario:

<pre>
uname -r
cat /etc/os-release
sudo apt update && sudo apt upgrade -y       # For Debian/Ubuntu
sudo yum check-update && sudo yum update -y  # For RHEL/CentOS
sudo reboot                                  # Only if kernel updated
systemctl status &lt;service-name&gt;
</pre>
---

</details>
<details>
<summary><strong>7. How do you check which process is using high CPU or memory in Linux?</strong></summary>

Use the <code>top</code> or <code>htop</code> command to identify the processes consuming the most system resources.

**Command:**
<pre><code>top
htop    # if installed
</code></pre>

**Real Scenario:**  
System is slow? Run <code>top</code> and check if any process is hitting 90–100% CPU or memory.
</details>



