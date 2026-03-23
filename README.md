# 🚀 CI/CD Pipeline Automation with Jenkins + Tomcat + Webhook

## 📌 Project Overview

This project demonstrates how to build a **CI/CD pipeline** using:

* Jenkins
* Apache Tomcat
* GitHub Webhooks

The pipeline automatically:

* Pulls code from GitHub
* Builds using Maven
* Deploys WAR file to Tomcat

This setup enables **fully automated deployment** on every code push.

---

## 🧱 Architecture

```
Developer → GitHub → Jenkins → Tomcat Server
                (Webhook Trigger)
```

* GitHub triggers Jenkins via webhook
* Jenkins builds the project
* Jenkins deploys to Tomcat

---

## 🚀 Technologies Used

* Jenkins
* Apache Tomcat
* Apache Maven
* GitHub
* Java

---

## 🔐 Key Features

* Automatic build trigger using GitHub Webhook
* Continuous Integration using Jenkins
* Automated WAR deployment to Tomcat
* Remote deployment using Tomcat Manager
* End-to-end CI/CD pipeline

---

## 📂 Project Structure

```
CI-CD-with-Jenkins-Tomacat/
│── src/main/webapp/
│── pom.xml
│── target/
│   └── *.war
```

---

## ⚙️ Setup Steps

### 1. Install Jenkins

Open:

```
http://<jenkins-ip>:8080
```

---

### 2. Install Required Plugins

* Git Plugin
* Maven Integration Plugin
*  Maven Invoker
* Deploy to Container Plugin
* GitHub Integration Plugin

---

### 3. Configure Jenkins Job

* Create Freestyle Project
* Add GitHub repo:

```
https://github.com/jerwin-18/CI-CD-with-Jenkins-Tomacat.git
```

* Enable:

```
GitHub hook trigger for GITScm polling
```

---

### 4. Configure Build Step

```
clean install
```

---

### 5. Configure Tomcat Deployment

Tomcat URL:

```
http://<tomcat-ip>:8080/manager/text
```

WAR File:

```
**/*.war
```

Context Path:

```
/home
```

---

### 6. Configure Tomcat User

Edit:

```
<TOMCAT_HOME>/conf/tomcat-users.xml
```

```
<role rolename="manager-script"/>
<user username="deploy" password="password" roles="manager-script"/>
```

---

### 7. Enable Remote Access

Edit:

```
<TOMCAT_HOME>/webapps/manager/META-INF/context.xml
```

Change:

```
allow=".*"
```

---

### 8. Configure GitHub Webhook

Payload URL:

```
http://<jenkins-ip>:8080/github-webhook/
```

Content type:

```
application/json
```

Event:

```
Just the push event
```

---

### 9. Deploy

* Push code to GitHub
* Jenkins triggers automatically
* WAR file deployed to Tomcat

---

## 🔍 Testing

| Test Case     | Expected Result     |
| ------------- | ------------------- |
| GitHub Push   | ✅ Jenkins triggered |
| Jenkins Build | ✅ Success           |
| Deployment    | ✅ WAR deployed      |
| Application   | ✅ Loads             |

---

## ⚠️ Common Issues & Fixes

### 403 Access Denied (Tomcat)

Cause: Missing role or wrong URL
Fix:

* Use `/manager/text`
* Add `manager-script` role

---

### Webhook Not Triggering

Cause: Wrong webhook URL
Fix:

```
http://<jenkins-ip>:8080/github-webhook/
```

---

### Deployment Failed

Cause: Incorrect credentials
Fix:

* Match Jenkins and Tomcat credentials

---

## ⚠️ Common Issues & How I Solved Them

403 Error:

* Fixed by adding `manager-script` role

Webhook Issue:

* Corrected webhook endpoint

Remote Access Issue:

* Updated `context.xml`

---

## 🎯 Learning Outcomes

* CI/CD pipeline implementation
* Jenkins automation
* Tomcat deployment
* GitHub webhook integration
* Debugging real-world issues

---

## 👨‍💻 Author

Jerwin Andro S

GitHub:
https://github.com/jerwin-18/CI-CD-with-Jenkins-Tomacat.git

