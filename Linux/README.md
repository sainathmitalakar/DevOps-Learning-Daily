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

### ✅ How to Add Daily Scenarios

- Copy one `<details>` block for each new scenario.  
- Replace the question, steps, and commands.  
- Commit changes — GitHub renders it **as an interactive collapsible tutorial page** automatically.

---

This structure will make your Linux README **look like a web page**, interactive and clean.  
Each new question you add will appear in the same style, ready for friends or colleagues to read and learn from.  
