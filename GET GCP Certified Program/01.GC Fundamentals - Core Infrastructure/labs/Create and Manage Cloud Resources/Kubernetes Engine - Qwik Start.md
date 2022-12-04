# Kubernetes Engine: Qwik Start

## GSP100

![Google Cloud self-paced labs logo](https://cdn.qwiklabs.com/GMOHykaqmlTHiqEeQXTySaMXYPHeIvaqa2qHEzw6Occ%3D)

## Overview

[Google Kubernetes Engine](https://cloud.google.com/kubernetes-engine/) (GKE) provides a managed environment for deploying, managing, and scaling your containerized applications using Google infrastructure. The Kubernetes Engine environment consists of multiple machines (specifically [Compute Engine](https://cloud.google.com/compute) instances) grouped to form a [container cluster](https://cloud.google.com/kubernetes-engine/docs/concepts/cluster-architecture). In this lab, you get hands-on practice with container creation and application deployment with GKE.

### Cluster orchestration with Google Kubernetes Engine

Google Kubernetes Engine (GKE) clusters are powered by the [Kubernetes](https://kubernetes.io/) open source cluster management system. Kubernetes provides the mechanisms through which you interact with your container cluster. You use Kubernetes commands and resources to deploy and manage your applications, perform administrative tasks, set policies, and monitor the health of your deployed workloads.

Kubernetes draws on the same design principles that run popular Google services and provides the same benefits: automatic management, monitoring and liveness probes for application containers, automatic scaling, rolling updates, and more. When you run your applications on a container cluster, you're using technology based on Google's 10+ years of experience with running production workloads in containers.

### Kubernetes on Google Cloud

When you run a GKE cluster, you also gain the benefit of advanced cluster management features that Google Cloud provides. These include:

* [Load balancing](https://cloud.google.com/compute/docs/load-balancing-and-autoscaling) for Compute Engine instances
* [Node pools](https://cloud.google.com/kubernetes-engine/docs/node-pools) to designate subsets of nodes within a cluster for additional flexibility
* [Automatic scaling](https://cloud.google.com/kubernetes-engine/docs/cluster-autoscaler) of your cluster's node instance count
* [Automatic upgrades](https://cloud.google.com/kubernetes-engine/docs/node-auto-upgrade) for your cluster's node software
* [Node auto-repair](https://cloud.google.com/kubernetes-engine/docs/how-to/node-auto-repair) to maintain node health and availability
* [Logging and Monitoring](https://cloud.google.com/kubernetes-engine/docs/how-to/logging) with Cloud Monitoring for visibility into your cluster

Now that you have a basic understanding of Kubernetes, you will learn how to deploy a containerized application with GKE in less than 30 minutes. Follow the steps below to set up your lab environment.

## Setup and requirements

### Before you click the Start Lab button

Read these instructions. Labs are timed and you cannot pause them. The timer, which starts when you click Start Lab, shows how long Google Cloud resources will be made available to you.

This hands-on lab lets you do the lab activities yourself in a real cloud environment, not in a simulation or demo environment. It does so by giving you new, temporary credentials that you use to sign in and access Google Cloud for the duration of the lab.

To complete this lab, you need:

* Access to a standard internet browser (Chrome browser recommended).

Note: Use an Incognito or private browser window to run this lab. This prevents any conflicts between your personal account and the Student account, which may cause extra charges incurred to your personal account.

* Time to complete the lab---remember, once you start, you cannot pause a lab.

Note: If you already have your own personal Google Cloud account or project, do not use it for this lab to avoid extra charges to your account.

### How to start your lab and sign in to the Google Cloud Console

1. Click the Start Lab button. If you need to pay for the lab, a pop-up opens for you to select your payment method. On the left is the Lab Details panel with the following:
  * The Open Google Console button
  * Time remaining
  * The temporary credentials that you must use for this lab
  * Other information, if needed, to step through this lab
2. Click Open Google Console. The lab spins up resources, and then opens another tab that shows the Sign in page.

_Tip:_ Arrange the tabs in separate windows, side-by-side.

Note: If you see the Choose an account dialog, click Use Another Account.
3. If necessary, copy the Username from the Lab Details panel and paste it into the Sign in dialog. Click Next.
4. Copy the Password from the Lab Details panel and paste it into the Welcome dialog. Click Next.

Important: You must use the credentials from the left panel. Do not use your Google Cloud Skills Boost credentials.

Note: Using your own Google Cloud account for this lab may incur extra charges.
5. Click through the subsequent pages:
  * Accept the terms and conditions.
  * Do not add recovery options or two-factor authentication (because this is a temporary account).
  * Do not sign up for free trials.

After a few moments, the Cloud Console opens in this tab.

Note: You can view the menu with a list of Google Cloud Products and Services by clicking the Navigation menu at the top-left. ![Navigation menu icon](https://cdn.qwiklabs.com/9vT7xPlxoNP%2FPsK0J8j0ZPFB4HnnpaIJVCDByaBrSHg%3D)

### Activate Cloud Shell

Cloud Shell is a virtual machine that is loaded with development tools. It offers a persistent 5GB home directory and runs on the Google Cloud. Cloud Shell provides command-line access to your Google Cloud resources.

1. Click Activate Cloud Shell ![Activate Cloud Shell icon](https://cdn.qwiklabs.com/ep8HmqYGdD%2FkUncAAYpV47OYoHwC8%2Bg0WK%2F8sidHquE%3D) at the top of the Google Cloud console.
2. Click Continue.

It takes a few moments to provision and connect to the environment. When you are connected, you are already authenticated, and the project is set to your PROJECT\_ID. The output contains a line that declares the PROJECT\_ID for this session:

    Your Cloud Platform project in this session is set to YOUR_PROJECT_ID

`gcloud` is the command-line tool for Google Cloud. It comes pre-installed on Cloud Shell and supports tab-completion.

1. (Optional) You can list the active account name with this command:

    gcloud auth list

Copied!

Output:

    ACTIVE: * ACCOUNT: student-01-xxxxxxxxxxxx@qwiklabs.net To set the active account, run: $ gcloud config set account `ACCOUNT`

1. (Optional) You can list the project ID with this command:

    gcloud config list project

Copied!

Output:

    [core] project = <project_ID>

Example output:

    [core] project = qwiklabs-gcp-44776a13dea667a6

[the gcloud CLI overview guide](https://cloud.google.com/sdk/gcloud).

## Task 1\. Set a default compute zone

Your [compute zone](https://cloud.google.com/compute/docs/regions-zones/#available) is an approximate regional location in which your clusters and their resources live. For example, `us-central1-a` is a zone in the `us-central1` region. Start a new session in Cloud Shell.

1. Set the default compute region,

    gcloud config set compute/region us-west3

Copied!

Expected output:

    Updated property [compute/region].

2. Set the default compute zone,

    gcloud config set compute/zone us-west3-b

Copied!

Expected output:

    Updated property [compute/zone].

## Task 2\. Create a GKE cluster

A [cluster](https://cloud.google.com/kubernetes-engine/docs/concepts/cluster-architecture) consists of at least one cluster master machine and multiple worker machines called nodes. Nodes are [Compute Engine virtual machine (VM) instances](https://cloud.google.com/compute/docs/instances/) that run the Kubernetes processes necessary to make them part of the cluster.

Note: Cluster names must start with a letter and end with an alphanumeric, and cannot be longer than 40 characters.

Run the following command:

1. Create a cluster

    gcloud container clusters create --machine-type=e2-medium --zone=us-west3-b lab-cluster 

Copied!

You can ignore any warnings in the output. It might take several minutes to finish creating the cluster.

Expected output:

    NAME: lab-cluster LOCATION: us-west3-b MASTER_VERSION: 1.22.8-gke.202 MASTER_IP: 34.67.240.12 MACHINE_TYPE: e2-medium NODE_VERSION: 1.22.8-gke.202 NUM_NODES: 3 STATUS: RUNNING

Click Check my progress to verify the objective.

Assessment Completed!

Create a GKE cluster

Assessment Completed!

## Task 3\. Get authentication credentials for the cluster

After creating your cluster, you need authentication credentials to interact with it.

1. Authenticate with the cluster:

    gcloud container clusters get-credentials lab-cluster 

Copied!

Expected output:

    Fetching cluster endpoint and auth data. kubeconfig entry generated for my-cluster.

## Task 4\. Deploy an application to the cluster

You can now deploy a containerized application to the cluster. For this lab, you'll run `hello-app` in your cluster.

GKE uses Kubernetes objects to create and manage your cluster's resources. Kubernetes provides the [Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) object for deploying stateless applications like web servers. [Service](https://kubernetes.io/docs/concepts/services-networking/service/) objects define rules and load balancing for accessing your application from the internet.

1. To create a new Deployment `hello-server` from the `hello-app` container image, run the following [kubectl create](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#create) command:

    kubectl create deployment hello-server --image=gcr.io/google-samples/hello-app:1.0

Copied!

Expected output:

    deployment.apps/hello-server created

This Kubernetes command creates a Deployment object that represents `hello-server`. In this case, `--image` specifies a container image to deploy. The command pulls the example image from a [Container Registry](https://cloud.google.com/container-registry/docs) bucket. `gcr.io/google-samples/hello-app:1.0` indicates the specific image version to pull. If a version is not specified, the latest version is used.

Click Check my progress to verify the objective.

Assessment Completed!

Create a new Deployment: hello-server

Assessment Completed!
2. To create a Kubernetes Service, which is a Kubernetes resource that lets you expose your application to external traffic, run the following [kubectl expose](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#expose) command:

    kubectl expose deployment hello-server --type=LoadBalancer --port 8080

Copied!

In this command:
  * `--port` specifies the port that the container exposes.
  * `type="LoadBalancer"` creates a Compute Engine load balancer for your container.

Expected output:

    service/hello-server exposed

3. To inspect the `hello-server` Service, run [kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#get):

    kubectl get service

Copied!

Expected output:

    NAME TYPE CLUSTER-IP EXTERNAL-IP PORT(S) AGE hello-server loadBalancer 10.39.244.36 35.202.234.26 8080:31991/TCP 65s kubernetes ClusterIP 10.39.240.1 433/TCP 5m13s

[Deleting a cluster](https://cloud.google.com/kubernetes-engine/docs/how-to/deleting-a-cluster).

Click Check my progress to verify the objective.

Assessment Completed!

Delete the cluster

Assessment Completed!