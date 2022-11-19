# Infrastructure Preview

30 minutes5 Credits

[](https://www.cloudskillsboost.google/focuses/79664562/reviews?parent=course_session)

[

](https://www.cloudskillsboost.google/focuses/79664562/reviews?parent=course_session)

## Overview

In this lab, you build a sophisticated deployment in minutes using Marketplace. This lab shows several of the Google Cloud infrastructure services in action and illustrates the power of the platform. It introduces technologies that are covered in detail later in the class.

## Objectives

In this lab, you learn how to perform the following tasks:

* Use Marketplace to build a Jenkins Continuous Integration environment.
* Verify that you can manage the service from the Jenkins UI.
* Administer the service from the Virtual Machine host through SSH.

### Qwiklabs setup

For each lab, you get a new GCP project and set of resources for a fixed time at no cost.

1. Make sure you signed into Qwiklabs using an incognito window.
2. Note the lab's access time (for example, ![img/time.png](https://cdn.qwiklabs.com/aZQJ4BT7uCmM9XR6BTXgTRP1Hfu1T7q6V%2BcnbdEsbpU%3D) and make sure you can finish in that time block.

There is no pause feature. You can restart if needed, but you have to start at the beginning.

1. When ready, click ![img/start_lab.png](https://cdn.qwiklabs.com/XE8x7uvQokyubNwnYKKc%2BvBBNrMlo5iNZiDDzQQ3Ddo%3D).
2. Note your lab credentials. You will use them to sign in to Cloud Platform Console. ![img/open_google_console.png](https://cdn.qwiklabs.com/32cCFOOhUz1MiXyZeArBWFlPA0K7NLLGCykpoimeM3o%3D)
3. Click Open Google Console.
4. Click Use another account and copy/paste credentials for this lab into the prompts.

If you use other credentials, you'll get errors or incur charges.

1. Accept the terms and skip the recovery resource page.

Do not click End Lab unless you are finished with the lab or want to restart it. This clears your work and removes the project.

## Task 1\. Use Marketplace to build a deployment

### Navigate to Marketplace

1. In the Cloud Console, on the Navigation menu (![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)), click Marketplace.
2. Locate the Jenkins deployment by searching for Jenkins packaged by Bitnami.
3. Click on the deployment and read about the service provided by the software.

Jenkins is an open-source continuous integration environment. You can define jobs in Jenkins that can perform tasks such as running a scheduled build of software and backing up data. Notice the software that is installed as part of Jenkins shown in the left side of the description.

The service you are using, Marketplace, is part of Google Cloud. The Jenkins template is developed and maintained by an ecosystem partner named Bitnami. Notice on the left side a field that says "Last updated." How recently was this template updated?

Google Cloud Marketplace lets you quickly deploy functional software packages by providing pre-defined templates with which Google Cloud service?

Terraform

Template Manager

checkDeployment Manager

Firestore

### Launch Jenkins

1. Click Launch.
2. Verify the deployment, accept the terms and services and click Deploy.

Note: It will take a minute or two for Deployment Manager to set up the deployment. You can watch the status as tasks are being performed. Deployment Manager is acquiring a virtual machine instance and installing and configuring software for you. You will see jenkins-1 has been deployed when the process is complete.

Deployment Manager is a Google Cloud service that uses templates written in a combination of YAML, python, and Jinja2 to automate the allocation of Google Cloud resources and perform setup tasks. Behind the scenes a virtual machine has been created. A startup script was used to install and configure software, and network Firewall Rules were created to allow traffic to the service.

Click _Check my progress_ to verify the objective.

Assessment Complete!

Launch Jenkins

Assessment Complete!

## Task 2\. Examine the deployment

In this section, you examine what was built in Google Cloud.

### View installed software and login to Jenkins

1. In the right pane, note the Admin user and Admin password values and add them to a text editor.
2. Click Visit the site to view the site in another browser tab. If you get an error, you might have to reload the page a couple of times.
3. Log in with the Admin user and Admin password values.

Note: If you get an http 404 error, then remove the /jenkins part from the site address and hit Enter. For example: http://35.238.162.236

1. After logging in, if you are asked to Customize Jenkins. Click _Install suggested plugins_, and then click _Restart_ after the installation is complete. The restart will take a couple of minutes.

Note: If you are getting an installation error, retry the installation and if it fails again, continue past the error and save and finish before restarting. The code of this solution is managed and supported by Bitnami.

### Explore Jenkins

1. In the Jenkins interface, in the left pane, click Manage Jenkins. Look at all of the actions available. You are now prepared to manage Jenkins. The focus of this lab is Google Cloud infrastructure, not Jenkins management, so seeing that this menu is available is the purpose of this step.
2. Leave the browser window open to the Jenkins service. You will use it in the next task.

Note: Now you have seen that the software is installed and working properly. In the next task you will open an SSH terminal session to the VM where the service is hosted, and verify that you have administrative control over the service.

## Task 3\. Administer the service

### View the deployment and SSH to the VM

1. In the Cloud Console, on the Navigation menu(![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)), click Deployment Manager.
2. Click jenkins-1\.
3. Click SSH to connect to the Jenkins server.

Note: The Console interface is performing several tasks for you transparently. For example, it has transferred keys to the virtual machine that is hosting the Jenkins software so that you can connect securely to the machine using SSH.

### Shut down and restart the services

1. In the SSH window, enter the following command to shut down all the running services:

    sudo /opt/bitnami/ctlscript.sh stop

Copied!

1. Refresh the browser window for the Jenkins UI. You will no longer see the Jenkins interface because the service was shut down.
2. In the SSH window, enter the following command to restart the services:

    sudo /opt/bitnami/ctlscript.sh restart

Copied!

1. Return to the browser window for the Jenkins UI and refresh it. You may have to do it a couple of times before the service is reachable.
2. In the SSH window, type `exit` to close the SSH terminal session.

## Task 4\. Review

In a few minutes you were able to launch a complete Continuous Integration solution. You demonstrated that you had user access through the Jenkins UI, and you demonstrated that you had administrative control over Jenkins by using SSH to connect to the VM where the service is hosted and by stopping and then restarting the services.