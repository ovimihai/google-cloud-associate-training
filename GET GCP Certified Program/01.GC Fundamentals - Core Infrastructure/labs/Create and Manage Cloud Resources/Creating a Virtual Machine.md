# Creating a Virtual Machine

40 minutes1 Credit

[](https://www.cloudskillsboost.google/focuses/3563/reviews?parent=catalog)

[

](https://www.cloudskillsboost.google/focuses/3563/reviews?parent=catalog)

## GSP001

![Google Cloud self-paced labs logo](https://cdn.qwiklabs.com/GMOHykaqmlTHiqEeQXTySaMXYPHeIvaqa2qHEzw6Occ%3D)

## Overview

Compute Engine lets you create virtual machines that run different operating systems, including multiple flavors of Linux (Debian, Ubuntu, Suse, Red Hat, CoreOS) and Windows Server, on Google infrastructure. You can run thousands of virtual CPUs on a system that is designed to be fast and to offer strong consistency of performance.

In this hands-on lab, you'll create virtual machine instances of various machine types using the Google Cloud Console and the `gcloud` command line. You'll also learn how to connect an NGINX web server to your virtual machine.

Although you can easily copy and paste commands from the lab to the appropriate place, we recommend that you type the commands yourself to reinforce your understanding of the core concepts.

### What you'll do

* Create a virtual machine with the Cloud Console.
* Create a virtual machine with the `gcloud` command line.
* Deploy a web server and connect it to a virtual machine.

### Prerequisites

* Familiarity with standard Linux text editors such as `vim`, `emacs`, or `nano` will be helpful.

## Setup

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

### Understanding Regions and Zones

Certain Compute Engine resources live in regions or zones. A region is a specific geographical location where you can run your resources. Each region has one or more zones. For example, the us-central1 region denotes a region in the Central United States that has zones `us-central1-a`, `us-central1-b`, `us-central1-c`, and `us-central1-f`.RegionsZones

Western USus-west1-a, us-west1-b

Central USus-central1-a, us-central1-b, us-central1-d, us-central1-f

Eastern USus-east1-b, us-east1-c, us-east1-d

Western Europeeurope-west1-b, europe-west1-c, europe-west1-d

Eastern Asiaasia-east1-a, asia-east1-b, asia-east1-c

Resources that live in a zone are referred to as zonal resources. Virtual machine Instances and persistent disks live in a zone. To attach a persistent disk to a virtual machine instance, both resources must be in the same zone. Similarly, if you want to assign a static IP address to an instance, the instance must be in the same region as the static IP.[Regions and zones documentation](https://cloud.google.com/compute/docs/regions-zones/)).

## Task 1\. Create a new instance from the Cloud Console

In this section, you'll learn how to create new pre-defined machine types with Compute Engine from the Cloud Console.

1. In the Cloud Console, on the Navigation menu (![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)), click Compute Engine \> VM Instances.

This may take a minute to initialize for the first time.
2. To create a new instance, click CREATE INSTANCE.
3. There are many parameters you can configure when creating a new instance. Use the following for this lab:FieldValueAdditional Information

NamegcelabName for the VM instance

Region"\>`<filled in at lab start>`For more information about regions, see the Compute Engine guide, [Regions and Zones](https://cloud.google.com/compute/docs/zones).

Zone"\>`<filled in at lab start>` \*Note: Remember the zone that you selected: you'll need it later. For more information about zones, see the Compute Engine guide, [Regions and Zones](https://cloud.google.com/compute/docs/zones).

SeriesE2Name of the series

Machine Type2 vCPUThis is an (e2-medium), 2-CPU, 4GB RAM instance. Several machine types are available, ranging from micro instance types to 32-core/208GB RAM instance types. For more information, see the Compute Engine guide, [About machine families](https://cloud.google.com/compute/docs/machine-types). Note: A new project has a default [resource quota](https://cloud.google.com/compute/docs/resource-quotas), which may limit the number of CPU cores. You can request more when you work on projects outside this lab.

Boot DiskNew 10 GB balanced persistent disk OS Image: Debian GNU/Linux 11 (bullseye)Several images are available, including Debian, Ubuntu, CoreOS, and premium images such as Red Hat Enterprise Linux and Windows Server. For more information, see Operating System documentation.

FirewallAllow HTTP trafficSelect this option in order to access a web server that you'll install later. Note: This will automatically create a firewall rule to allow HTTP traffic on port 80\.

1. Click Create.

It should take about a minute for the machine to be created. After that, the new virtual machine is listed on the VM Instances page.
2. To use SSH to connect to the virtual machine, in the row for your machine, click SSH.

This launches an SSH client directly from your browser.[Connect to Linux VMs using Google tools](https://cloud.google.com/compute/docs/instances/connecting-to-instance).


```
gcloud compute instances create gcelab --project=qwiklabs-gcp-03-4fa7d2db3bbf --zone=us-west4-c --machine-type=e2-medium --network-interface=network-tier=PREMIUM,subnet=default --metadata=enable-oslogin=true --maintenance-policy=MIGRATE --provisioning-model=STANDARD --service-account=102027983038-compute@developer.gserviceaccount.com --scopes=https://www.googleapis.com/auth/devstorage.read_only,https://www.googleapis.com/auth/logging.write,https://www.googleapis.com/auth/monitoring.write,https://www.googleapis.com/auth/servicecontrol,https://www.googleapis.com/auth/service.management.readonly,https://www.googleapis.com/auth/trace.append --tags=http-server --create-disk=auto-delete=yes,boot=yes,device-name=gcelab,image=projects/debian-cloud/global/images/debian-11-bullseye-v20220920,mode=rw,size=10,type=projects/qwiklabs-gcp-03-4fa7d2db3bbf/zones/us-west4-c/diskTypes/pd-balanced --no-shielded-secure-boot --shielded-vtpm --shielded-integrity-monitoring --reservation-affinity=any
```

## Task 2\. Install an NGINX web server

Now you'll install an NGINX web server, one of the most popular web servers in the world, to connect your virtual machine to something.

1. Update the OS:

     sudo apt-get update

Copied!

Expected output:

     Get:1 http://security.debian.org stretch/updates InRelease [94.3 kB] Ign http://deb.debian.org strech InRelease Get:2 http://deb.debian.org strech-updates InRelease [91.0 kB] ...

2. Install NGINX:

     sudo apt-get install -y nginx

Copied!

Expected output:

     Reading package lists... Done Building dependency tree Reading state information... Done The following additional packages will be installed: ...

3. Confirm that NGINX is running:

     ps auwx | grep nginx

Copied!

Expected output:

     root 2330 0.0 0.0 159532 1628 ? Ss 14:06 0:00 nginx: master process /usr/sbin/nginx -g daemon on; master_process on; www-data 2331 0.0 0.0 159864 3204 ? S 14:06 0:00 nginx: worker process www-data 2332 0.0 0.0 159864 3204 ? S 14:06 0:00 nginx: worker process root 2342 0.0 0.0 12780 988 pts/0 S+ 14:07 0:00 grep nginx

4. To see the web page, return to the Cloud Console and click the External IP link in the row for your machine, or add the External IP value to `http://EXTERNAL_IP/` in a new browser window or tab.

This default web page should open:

![Default nginx page](https://cdn.qwiklabs.com/%2BOL6V6asztPiJZBeMO0xqc%2FiAX8iJfSTr4wDkJmKQu4%3D)

To check your progress in this lab, click Check my progress below. A checkmark means you're successful.

Create a Compute Engine instance and add an NGINX Server to your instance with necessary firewall rules.

## Task 3\. Create a new instance with gcloud

Instead of using the Cloud Console to create a virtual machine instance, you can use the command line tool `gcloud`, which is pre-installed in [Google Cloud Shell](https://cloud.google.com/developer-shell/#how_do_i_get_started). Cloud Shell is a Debian-based virtual machine loaded with all the development tools you'll need (`gcloud`, `git`, and others) and offers a persistent 5-GB home directory.[gcloud command line tool guide](https://cloud.google.com/sdk/gcloud/).

1. In the Cloud Shell, use `gcloud` to create a new virtual machine instance from the command line:

     gcloud compute instances create gcelab2 --machine-type e2-medium --zone 

Copied!

Expected output:

     Created [...gcelab2]. NAME: gcelab2 ZONE: MACHINE_TYPE: e2-medium PREEMPTIBLE: INTERNAL_IP: 10.128.0.3 EXTERNAL_IP: 34.136.51.150 STATUS: RUNNING

To check your progress in this lab, click Check my progress below. A checkmark means you're successful.

Create a new instance with gcloud.

The new instance has these default values:
  * The latest [Debian 11 (bullseye)](https://cloud.google.com/compute/docs/images#debian) image.
  * The `e2-medium` [machine type](https://cloud.google.com/compute/docs/machine-types).
  * A root persistent disk with the same name as the instance; the disk is automatically attached to the instance.

When you're working in your own project you can specify a [custom machine type](https://cloud.google.com/compute/docs/instances/creating-instance-with-custom-machine-type).
2. To see all the defaults, run:

     gcloud compute instances create --help

Copied!

**Note:** You can set the default region and zones that `gcloud` uses if you are always working within one region/zone and you don't want to append the `--zone` flag every time.

To do this, run these commands:

`gcloud config set compute/zone ...`

`gcloud config set compute/region ...`
3. To exit `help`, press CTRL + C.
4. In the Cloud Console, on the Navigation menu, click Compute Engine \> VM instances. our 2 new instances should be listed.
5. You can also use SSH to connect to your instance via `gcloud`. Make sure to add your zone, or omit the `--zone` flag if you've set the option globally:

     gcloud compute ssh gcelab2 --zone 

Copied!

6. Type Y to continue.

     Do you want to continue? (Y/n)

7. Press ENTER through the passphrase section to leave the passphrase empty.

     Generating public/private rsa key pair. Enter passphrase (empty for no passphrase)

8. After connecting, disconnect from SSH by exiting from the remote shell:

     exit

Copied!

## Task 4\. Test your knowledge

Test your knowledge about Google Cloud by taking our quiz. (Please select multiple correct options if necessary.)

Through which of the following ways can you create a VM instance in Compute Engine?

checkThe Cloud Console

checkThe gcloud command line tool





## Windows version
```
gcloud compute instances create instance-1 --project=qwiklabs-gcp-02-bb1999ec362e --zone=us-east1-b --machine-type=n1-standard-1 --network-interface=network-tier=PREMIUM,subnet=default --metadata=enable-oslogin=true --maintenance-policy=MIGRATE --provisioning-model=STANDARD --service-account=998961309545-compute@developer.gserviceaccount.com --scopes=https://www.googleapis.com/auth/devstorage.read_only,https://www.googleapis.com/auth/logging.write,https://www.googleapis.com/auth/monitoring.write,https://www.googleapis.com/auth/servicecontrol,https://www.googleapis.com/auth/service.management.readonly,https://www.googleapis.com/auth/trace.append --create-disk=auto-delete=yes,boot=yes,device-name=instance-1,image=projects/windows-cloud/global/images/windows-server-2012-r2-dc-v20220915,mode=rw,size=50,type=projects/qwiklabs-gcp-02-bb1999ec362e/zones/us-east1-b/diskTypes/pd-balanced --no-shielded-secure-boot --shielded-vtpm --shielded-integrity-monitoring --reservation-affinity=any
```

```
gcloud compute reset-windows-password instance-1 --zone us-east1-b --user admin
````

add `default-allow-rdp` firewall rule
