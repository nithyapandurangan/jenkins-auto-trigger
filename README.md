# Automating Build Triggers in Jenkins

## Overview
This project demonstrates how to automate Jenkins builds using different trigger mechanisms, including GitHub Webhooks, scheduled CRON jobs, and manual triggers.

## Prerequisites
- Jenkins installed and running on Windows (`http://localhost:8080`)
- A GitHub account and repository
- Git installed on your system
- ngrok (for local webhook testing, if required)

## Steps to Set Up

### 1. Repository Setup
1. Create a new GitHub repository (e.g., `jenkins-auto-trigger`).
2. Add a basic script (e.g., `build.py` or `build-script.sh`).
3. Clone the repository to your local machine.

### 2. Jenkins Configuration
1. Create a new **Freestyle project** in Jenkins (`AutoBuildTrigger`).
2. Configure it to pull the code from your GitHub repository.
3. Add credentials if the repository is private.

### 3. Build Triggers
#### **GitHub Webhook**
1. In **GitHub**, go to `Settings → Webhooks → Add Webhook`.
2. Set the **Payload URL** to: `http://your-jenkins-server/github-webhook/` (or use ngrok if local).
3. Select **Just the push event** and click **Add Webhook**.

#### **Scheduled Trigger (CRON)**
1. In Jenkins, go to **AutoBuildTrigger → Configure**.
2. Enable **Build periodically** and set the CRON schedule:
   ```
   H/30 * * * *
   ```
   (Runs every 30 minutes)

#### **Manual Trigger**
1. In Jenkins, go to **Dashboard → AutoBuildTrigger**.
2. Click **Build Now** to manually trigger a build.

### 4. Verification
- **Push a commit** to GitHub and verify that Jenkins triggers a build via webhook.
- Check if the **scheduled trigger** runs as expected.
- Manually trigger a build and compare results.

### 5. Optional: Notifications
- Configure **email notifications** using SMTP.
- Set up **Slack notifications** using a webhook.

## Author
Nithya Pandurangan
