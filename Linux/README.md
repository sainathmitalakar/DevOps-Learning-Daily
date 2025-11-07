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
<summary><b>3. How do you check running Docker containers on a Linux server?</b></summary>

### Steps:
<ul>
<li>List all running containers.</li>
<li>Inspect logs if a container is not behaving.</li>
<li>Restart or stop containers as needed.</li>
<li>Monitor resource usage per container.</li>
</ul>

### Commands used:

<pre>
docker ps
docker logs &lt;container-id&gt;
docker restart &lt;container-id&gt;
docker stats
</pre>

</details>

---

### ✅ How to Add Daily Scenarios

- Copy one `<details>` block for each new scenario.  
- Replace the question, steps, and commands.  
- Commit changes — GitHub renders it **as an interactive collapsible tutorial page** automatically.

---

This gives you a **clean webpage-like UI** for all your Linux DevOps scenarios.  
When you commit, all collapsible sections, code blocks, and lists render **beautifully** on GitHub.  

---

If you want, I can **convert your entire Linux README with all current scenarios into this webpage style**, so it’s ready to go for daily updates.  

Do you want me to do that?
