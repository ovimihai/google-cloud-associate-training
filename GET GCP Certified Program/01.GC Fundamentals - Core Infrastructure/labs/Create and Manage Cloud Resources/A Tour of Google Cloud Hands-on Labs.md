# A Tour of Google Cloud Hands-on Labs | Google Cloud Skills Boost


## GSP282![Google Cloud self-paced labs logo](https://cdn.qwiklabs.com/GMOHykaqmlTHiqEeQXTySaMXYPHeIvaqa2qHEzw6Occ%3D)

## Overview

[Google Cloud](https://cloud.google.com/) is a suite of cloud services hosted on Google's infrastructure. From computing and storage, to data analytics, machine learning, and networking, Google Cloud offers a wide variety of services and APIs that can be integrated with any cloud-computing application or project, from personal to enterprise-grade.

In this introductory-level lab, you will take your first steps with Google Cloud by getting hands-on practice with the [Cloud Console](https://cloud.google.com/cloud-console/)---an in-browser UI that lets you access and manage Google Cloud services. You will identify key features of Google Cloud and also learn about the details of the lab environment. If you are new to cloud computing or looking for an overview of Google Cloud and Qwiklabs, you are in the right place. Read on to learn about the specifics of this lab and areas that you will get hands-on practice with.

### What you will learn

In this lab, you will do the following:

* Learn about the labs platform, and identify key features of a lab environment.
* Learn how to access the Cloud Console with specific credentials.
* Learn about Google Cloud projects, and identify common misconceptions about them.
* Learn how to use the Google Cloud Navigation menu to identify types of Google Cloud services.
* Learn about basic roles, and use the Cloud IAM service to inspect actions available to specific users.
* Learn about the API library, and examine its chief features.

### Prerequisites

This is an _introductory-level_ lab and the first lab you should take if you're unfamiliar with Google Cloud. If you are already experienced with Cloud Console, consider taking one of the following labs:

If you decide to take one, be sure to **end this lab now**.

If you have a personal or corporate Google Cloud account or project, sign out of that account. If you stay logged in to your personal/corporate account and run the lab in the same browser, your credentials could get confused, resulting in getting logged out of the lab accidentally.

If you are using a Pixelbook, run your lab an Incognito window.

## Lab fundamentals

### Features and components

Regardless of topic or expertise level, all labs share a common interface. The lab that you're taking should look similar to this:![lab_view.png](https://cdn.qwiklabs.com/Gx5QWak6EsvW0PQURmiMyf10sLtl2AT%2BUSrD04WuCzY%3D)**Note**: You are not taking the "Creating a Virtual Machine" lab shown in the image; it is used as an example to highlight common features across labs.

Read the following lab component definitions, and then locate them in the interface.

#### Start Lab (button)

Clicking this button creates a temporary Google Cloud environment, with all the necessary services and credentials enabled, so you can get hands-on practice with the lab's material. This also starts a countdown timer.

#### Credit

The price of a lab. 1 Credit is _usually_ equivalent to 1 US dollar (discounts are available when you purchase credits in bulk). Some introductory-level labs (like this one) are free. The more specialized labs cost more because they involve heavier computing tasks and demand more Google Cloud resources.

#### Time

Specifies the amount of time you have to complete a lab. When you click the Start Lab button, the timer will count down until it reaches 00:00:00\. When it does, your temporary Google Cloud environment and resources are deleted. Ample time is given to complete a lab, but make sure you don't work on something else while a lab is running: you risk losing all of your hard work!

#### Score

Many labs include a score. This feature is called "activity tracking" and ensures that you complete specified steps in a lab. To pass a lab with activity tracking, you need to complete all the steps _in order_. Only then will you receive completion credit.

### Reading and following instructions

This browser tab contains the lab instructions. When you start a lab, the lab environment in this case, the Google Cloud Console user interface opens in a new browser tab. You will need to switch between the two browser tabs to read the instructions and then perform the tasks. Depending on your physical computer setup, you could also move the two tabs to separate monitors.

### Test your understanding

Answer the following multiple choice questions to reinforce your understanding of the concepts we've covered so far.

## Accessing the Cloud Console

### Start the lab

* Now that you understand the key features and components of a lab, click **Start Lab**.

It may take a moment for the Google Cloud environment and credentials to spin up. When the timer starts counting down and the Start Lab button changes to a red End Lab button, everything is in place and you're ready to sign in to the Cloud Console.**Note**: Do not click the End Lab button until you have completed all the tasks in the lab. When you click the button, your temporary credentials are invalidated and you won't be able to access the work you've done throughout the lab. You must click this button when you finish; if you do not, you won't be able to take another lab. (Qwiklabs has protections in place to prevent concurrent enrollment.)

### Connection Details pane

Now that your lab instance is up and running, look at the left pane. It contains an Open Google Console button, credentials (username and password), and a Project ID field.![Open_Google_Console.png](https://cdn.qwiklabs.com/%2FtHp4GI5VSDyTtdqi3qDFtevuY014F88%2BFow%2FadnRgE%3D)**Note**: Your credentials will resemble but not match the image; every lab instance generates new temporary credentials.

Now examine each of these components.

#### Open Google Console

This button opens the [Cloud Console](https://cloud.google.com/cloud-console/): the web console and central development hub for Google Cloud. You will do the majority of your work in Google Cloud from this interface.

#### Project ID

A [Google Cloud project](https://cloud.google.com/docs/overview/#projects) is an organizing entity for your Google Cloud resources. It often contains resources and services; for example, it may hold a pool of virtual machines, a set of databases, and a network that connects them together. Projects also contain settings and permissions, which specify security rules and who has access to what resources.

A _Project ID_ is a unique identifier that is used to link Google Cloud resources and APIs to your specific project. Project IDs are unique across Google Cloud: there can be only one **qwiklabs-gcp-xxx....**, which makes it globally identifiable.

#### Username and Password

These credentials represent an identity in the Cloud Identity and Access Management (Cloud IAM) service. This identity has access permissions (a role or roles) that allow you to work with Google Cloud resources in the project you've been allocated. These credentials are _temporary_ and will only work for the access time of the lab. When the timer reaches 00:00:00, you will no longer have access to your Google Cloud project with those credentials.

### Task 1\. Sign in to Google Cloud

Now that you have a better understanding of the Connection Details pane, use its contents to sign in to the Cloud Console.

1. Click **Open Google Console**.

This opens the Google Cloud sign-in page in a new browser tab.![SignInPage.png](https://cdn.qwiklabs.com/VkUIAFY2xX3zoHgmWqYKccRLwFrR4BfARLd5ojmlbhs%3D)

If you've ever signed in to a Google application like Gmail, this page should look familiar.

**_Tip_** Open the tabs in separate windows, side-by-side.

1. Copy the **Username** from the Connection Details pane, paste it in the **Email or phone** field, and click **Next**.

_Wait! Make sure to use the googlexxxxxx\_student@qwiklabs.net email to sign in, NOT your personal or company email address!_The username that resembles googlexxxxxx\_student@qwiklabs.net is a Google account that was created for your use as a student. It has a specific domain name, which is "qwiklabs.net," and has been assigned IAM roles that allow you to access the Google Cloud Project that you have been provisioned.

1. Copy the **Password** from the Connection Details pane, paste it in the **Password** field, and click **Next**.
2. Click **I understand** to indicate your acknowledgement of Google's terms of service and privacy policy.
3. On the **Protect your account** page, click **Confirm**.

Because this is a temporary account, don't worry about updating recovery phone numbers or emails.

1. On the **Welcome student!** page, check **Terms of Service** to agree to Google Cloud's terms of service, and click **Agree and continue**.

You've successfully accessed the Cloud Console with your student credentials! Your page should now look like this:![35a55968748df7c0.png](https://cdn.qwiklabs.com/vPsOw690IZhUlPPxZk3asDaXQBRVZRiyr%2B6nBXCqEf4%3D)

### Test your understanding

Answer the following multiple choice questions to reinforce your understanding of the concepts covered so far.

Now that you have signed in to the Cloud Console and understand the basics of your credentials, it's time to learn a little bit more about Google Cloud projects.

## Projects in the Cloud Console

Google Cloud projects were explained in the section about the contents of the Connection Details pane. Here's the definition once again:

A [Google Cloud project](https://cloud.google.com/docs/overview/#projects) is an organizing entity for your Google Cloud resources. It often contains resources and services; for example, it may hold a pool of virtual machines, a set of databases, and a network that connects them together. Projects also contain settings and permissions, which specify security rules and who has access to what resources.

The upper-left corner of the central pane contains a card labeled _Project info_ that looks like this:![76370a4185212435.png](https://cdn.qwiklabs.com/kaHKc2t7OyP7YUPOj4Eqw0nuUXQvt0iUypsuaeqkzKw%3D)

Your project has a _name_, _ID_, and _number_. These identifiers are frequently used when interacting with Google Cloud services. You are working with one project to get experience with a specific service or feature of Google Cloud.

### Task 2\. View all projects

You actually have access to more than one Google Cloud project. In fact, in some labs you may be given more than one project in order to complete the assigned tasks.

1. In the Google Cloud Console title bar, next to your project name, click the drop-down menu.
2. In the **Select a project** dialog, click **All**. The resulting list of projects includes a "Qwiklabs Resources" project.![66c73e22ea578f78.png](https://cdn.qwiklabs.com/1hqteUty9xHbSdnkgtI4ZrrHDAG8pHWKAEUUjNzLk2M%3D)**Do not switch over to the Qwiklabs Resources project at this point!** However, you may use it later in other labs.

It's not uncommon for large enterprises or experienced users of Google Cloud to have dozens to thousands of Google Cloud projects. Organizations use Google Cloud in different ways, so projects are a good method for organizing cloud computing services (by team or product, for example.)

The "Qwiklabs Resources" project contains files, datasets, and machine images for certain labs and can be accessed from every Google Cloud lab environment. It's important to note that "Qwiklabs Resources" is shared (read only) with all student users, which means that you cannot delete or modify it.

The Google Cloud project that you are working with is _temporary_, which means that the project and everything it contains will be deleted when the lab ends. Whenever you start a new lab, you will be given access to one or more new Google Cloud projects, and there (not "Qwiklabs Resources") is where you will run all of the lab steps.

### Test your understanding

Answer the following multiple choice questions to reinforce your understanding of the concepts covered so far.

## Navigation menu and services

The Google Cloud Console title bar also contains a button labeled with a three-line icon:![818684f8e0d0a523.png](https://cdn.qwiklabs.com/jNaEVX1xXeOOasukmY%2B9mcktmn9gjkwgNAJEkBlIYbI%3D)

Clicking this button opens (or hides) the _Navigation menu_ that provides quick access to Google Cloud's core services.

* If the menu isn't open, click the button now and scroll through to see the types of services available:![5012e407e81c6d07.png](https://cdn.qwiklabs.com/gk6CVCz3LGXvViYQ%2FZUp%2Bu1VqI0DBrDAZh7kToRN20Q%3D)

There are seven categories of Google Cloud services:

* **Compute:** A variety of machine types that support any type of workload. The different computing options let you decide how much control you want over operational details and infrastructure.
* **Storage:** Data storage and database options for structured or unstructured, relational or non relational data.
* **Networking:** Services that balance application traffic and provision security rules.
* **Cloud Operations:** A suite of cross-cloud logging, monitoring, trace, and other service reliability tools.
* **Tools:** Services that help developers manage deployments and application build pipelines.
* **Big Data:** Services that allow you to process and analyze large datasets.
* **Artificial Intelligence:** A suite of APIs that run specific artificial intelligence and machine learning tasks on Google Cloud.

[This link](https://cloud.google.com/docs/overview/cloud-platform-services#top_of_page) takes you to documentation that covers each of these categories in more detail.

## Roles and permissions

Earlier you learned that, in addition to cloud computing services, Google Cloud also contains a collection of permissions and roles that define who has access to what resources. You can use the [Cloud Identity and Access Management (Cloud IAM)](https://cloud.google.com/iam/) service to inspect and modify these roles and permissions.

### Task 3\. View your roles and permissions

1. On the **Navigation menu** (![Navigation menu](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)), click **IAM & Admin**. This opens a page that contains a list of users and specifies permissions and roles granted to specific accounts.![87534f555ed17b88.png](https://cdn.qwiklabs.com/v5er%2BfG4yURAeD9YUOKNuDgtD9KdMi9Sg2Ph9XThkZA%3D)

1. Find the "@qwiklabs" username you signed in with:![principal1.png "Find Qwiklabs Member"](https://cdn.qwiklabs.com/VpeV7knPXEDf39QBcfOJuAZpDB7zPgjzMSFmmCy2avk%3D)

The _Principal_ column displays `googlexxxxxx_student@qwiklabs.net` (which matches the username you signed in with). The _Name_ column displays `student XXXXXXXX`. The _Role_ column displays `Editor`, which is one of three _basic roles_ offered by Google Cloud. Basic roles set project-level permissions and, unless otherwise specified, control access and management to all Google Cloud services.

The following table pulls definitions from the [roles documentation](https://cloud.google.com/iam/docs/understanding-roles/#primitive%5C_roles), which gives a brief overview of viewer, editor, and owner role permissions:Role NamePermissions

roles/viewerPermissions for read-only actions that do not affect state, such as viewing (but not modifying) existing resources or data.

roles/editorAll viewer permissions, plus permissions for actions that modify state, such as changing existing resources.

roles/ownerAll editor permissions and permissions for the following actions: manage roles and permissions for a project and all resources within the project; set up billing for a project.

As an editor, you can create, modify, and delete Google Cloud resources. However, you can't add or delete members from Google Cloud projects.

### Test your understanding

Answer the following multiple choice questions to reinforce your understanding of the concepts covered so far.

## APIs and services

Google Cloud APIs are a key part of Google Cloud. Like services, the 200+ APIs, in areas that range from business administration to machine learning, all easily integrate with Google Cloud projects and applications.

APIs are _application programming interfaces_ that you can call directly or via the client libraries. Cloud APIs use resource-oriented design principles as described in the [API Design Guide](https://cloud.google.com/apis/design/).

When a lab provides a new Google Cloud project for a lab instance, it enables most APIs automatically so you can quickly start work on the lab's tasks. When you create your own Google Cloud projects outside of the lab environment, you will have to enable certain APIs yourself.

Most Cloud APIs provide you with detailed information on your project's usage of that API, including traffic levels, error rates, and even latencies, which helps you quickly triage problems with applications that use Google services.

### Task 4\. View available APIs

1. On the **Navigation menu** (![Navigation menu](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)), click **APIs & Services \> Library**. The left pane, under the header **CATEGORY**, displays the different categories available.![apis.gif](https://cdn.qwiklabs.com/IhN1xAfMsp0KrMIwX50LGtlzcsup%2BfK45UA1wseaaa4%3D)

1. In the API search bar, type **Dialogflow**, and then click **Dialogflow API**. The Dialogflow description page opens.![dialogflow.png](https://cdn.qwiklabs.com/TJxda7OL7Z8mAPtAWRFkf16dH2KSGWP%2FS0cEvzofT%2Fw%3D)

The Dialogflow API allows you to build rich conversational applications (e.g., for Google Assistant) without having to understand the underlying machine learning and natural language schema.

1. Click **Enable**.
2. Click the back button in your browser to verify that the API is now enabled.![enabled.png](https://cdn.qwiklabs.com/eTgnbsNvLaqrex7qumvUuzQEc114GwncM%2FV8xL4j594%3D)

1. Click **Try this API**. A new browser tab displays documentation for the Dialogflow API. Explore this information, and close the tab when you're finished.
2. To return to the main page of the Cloud Console, on the **Navigation menu**, click **Cloud overview**.**Note: **You will now encounter a unique feature on Qwiklabs called as Activity Tracking that assesses completion of a task. As you complete tasks and verify these with '**Check my progress**' tests, notice that your score increases in the box in the upper right corner. This scoring determines lab completion towards the accomplishment of badges and credentials. Scoring also contributes to leaderboard position in lab games. In this case, Activity Tracking will verify if you completed enabling the Dialogflow API.

Click **Check my progress** to verify the objective. Enable the Dialogflow API

If you're interested in learning more about APIs, open the [Google APIs Explorer](https://developers.google.com/apis-explorer/#p/). Google also has a lab, [APIs Explorer: Qwik Start](https://google.qwiklabs.com/catalog_lab/1241), that will give you hands-on experience with the tool, using a simple example.

### Test your understanding

Answer the following multiple choice question to reinforce your understanding of the concepts covered so far.

## Ending your lab

Now that you're finished with the lab, click **End Lab** and then click **Submit** to confirm it.![end_lab.gif](https://cdn.qwiklabs.com/W%2B4SnUeJ5uNFmTjaRFdsBrUHr0SSyl%2BFkgc3i%2B6Eyxc%3D)