❓Scenario 2: Application Fails to Start Due to Port Already in Use

Interviewer:
Your application failed to start, and the error says: “Port 8080 already in use.”
How would you handle this situation?

Candidate Answer:
First, I’ll check which process is using port 8080:

sudo lsof -i :8080


or

sudo netstat -tuln | grep 8080


This will show which process or service is bound to that port.
I’ll note down its PID and name.

If it’s an old or crashed service that didn’t shut down properly, I’ll stop it:

sudo kill -9 <PID>


If it’s a valid service (for example, another instance of the same app),
I’ll update my app’s configuration file to use another port (e.g., 8081)
and restart the application:

sudo systemctl restart myapp


To confirm the app is running on the new port:

sudo netstat -tuln | grep 8081


Key Takeaway:
Always check which process is using the port before killing it.
In production, coordinate with the team before making any changes.
