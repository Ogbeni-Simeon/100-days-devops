# Day 11 – Deploying a Java Application on Tomcat

## Overview
This day focused on deploying a **Java web application** using the **Tomcat application server** on App Server 3.

The task covered:
- Installing and managing a Java application server  
- Modifying service configuration safely  
- Deploying a WAR file as a ROOT application  
- Verifying application availability on a custom port  

This exercise introduced core concepts of **application server configuration and deployment**, which are fundamental in real-world DevOps workflows.

---

## Task Summary

The requirements were:

1. Install Tomcat on App Server 3  
2. Configure Tomcat to run on **port 5000**  
3. Deploy a provided `ROOT.war` file  
4. Ensure the application works at the base URL:

```bash
curl http://stapp03:5000
````

---

## Step 1 – Install Tomcat

```bash
sudo yum install -y tomcat
```

This installed:

* Tomcat binaries
* Default configuration files
* A systemd service for managing Tomcat

---

## Step 2 – Configure Tomcat to Use Port 5000

By default, Tomcat listens on port **8080**.
The task required changing this to **5000**.

Instead of using an interactive editor, the configuration was modified using a non-interactive and automation-friendly method:

```bash
sudo sed -i 's/port="8080"/port="5000"/' /etc/tomcat/server.xml
```

Verification:

```bash
grep 5000 /etc/tomcat/server.xml
```

This confirmed the connector was now configured to listen on port 5000.

---

## Step 3 – Start and Enable Tomcat

```bash
sudo systemctl start tomcat
sudo systemctl enable tomcat
```

Service status check:

```bash
sudo systemctl status tomcat
```

Expected state:

```
Active: active (running)
```

---

## Step 4 – Deploy the ROOT Application

The provided application archive was named:

```
ROOT.war
```

It was placed into Tomcat’s deployment directory:

```bash
sudo cp /tmp/ROOT.war /var/lib/tomcat/webapps/ROOT.war
sudo chown tomcat:tomcat /var/lib/tomcat/webapps/ROOT.war
```

Naming the file `ROOT.war` is critical because:

* It deploys the application at the **base URL**
* No context path (e.g. `/app`) is required

---

## Step 5 – Restart Tomcat to Deploy the Application

```bash
sudo systemctl restart tomcat
```

This triggered Tomcat to unpack and deploy the new application.

---

## Step 6 – Verify the Application

```bash
curl http://stapp03:5000
```

Observed output included:

```html
<h2>Welcome to xFusionCorp Industries!</h2>
```

This confirmed:

* Tomcat was listening on port 5000
* The application was deployed correctly
* The ROOT context was working as expected

---

## Final Outcome

* Tomcat installed and running
* Port changed from 8080 to 5000
* ROOT application deployed successfully
* Application accessible at base URL
* Task completed successfully

---

## Key Concepts Learned

### 1. Changing Default Service Ports

Application servers often run on default ports.
Knowing how to safely modify service configuration is essential.

---

### 2. ROOT vs Context-Based Deployment

Deploying as `ROOT.war` allows:

* Access via `http://host:port/`
* No additional URL path required

This is a common production requirement.

---

### 3. Non-Interactive Configuration Editing

Using tools like `sed` instead of interactive editors:

* Avoids terminal issues
* Works well in automation
* Is safer and reproducible

---

### 4. Verifying with curl

Using `curl` to validate application health is a core DevOps habit and works well in:

* Automation
* CI pipelines
* Monitoring scripts

---

## Personal Reflection

Day 11 introduced real application deployment concepts:

* Managing an application server
* Modifying production configuration
* Understanding how deployment paths affect URLs
* Verifying service health programmatically

This task felt like a direct simulation of how backend applications are deployed in production environments.
