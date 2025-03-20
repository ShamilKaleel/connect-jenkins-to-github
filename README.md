# Jenkins GitHub Webhook Integration

This repository demonstrates how to integrate Jenkins with GitHub using a webhook to trigger builds automatically.

## Prerequisites

Before setting up the webhook, ensure you have the following:
- A running Jenkins server (You can use **ngrok** to expose your local Jenkins instance to the internet)
- A GitHub repository
- The **GitHub plugin** installed in Jenkins
- A Jenkins job configured to build the project

## Step-by-Step Guide

### 1. Configure Jenkins
1. Open Jenkins and navigate to **Manage Jenkins > Configure System**.
2. Scroll down to the **GitHub** section and add your GitHub credentials if required.
3. Ensure the **GitHub plugin** is installed.

### 2. Set Up the Jenkins Job
1. In Jenkins, create a new **Freestyle Project** or **Pipeline Job**.
2. Under **Source Code Management**, select **Git** and provide the repository URL.
3. Under **Build Triggers**, check **GitHub hook trigger for GITScm polling**.
4. Save the configuration.

### 3. Create a GitHub Webhook
1. Go to your GitHub repository.
2. Navigate to **Settings > Webhooks**.
3. Click **Add webhook**.
4. Set the following details:
   - **Payload URL**: `http://<JENKINS_URL>/github-webhook/` (Replace `<JENKINS_URL>` with your Jenkins instance URL)
   - **Content type**: `application/json`
   - **Trigger events**: Select **Just the push event** or other events as needed.
5. Click **Add webhook**.

### 4. Test the Webhook
1. Make a commit and push changes to the repository.
2. Navigate to **Jenkins > Your Job > Build History** to see if the build is triggered.
3. Check the **GitHub Webhooks** section under repository settings for delivery logs.

## Troubleshooting
- Ensure Jenkins is accessible from the internet or within your network. You can use **ngrok** to expose your local Jenkins instance to the internet.
- Verify that the webhook URL is correct.
- Check Jenkins logs for errors related to webhooks.
- Ensure the GitHub plugin is installed and configured properly.

## Conclusion
By setting up a webhook, you automate the process of triggering Jenkins builds whenever changes are pushed to the repository, improving CI/CD efficiency.
