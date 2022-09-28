# Google Cloud Fundamentals: Getting Started with Cloud Marketplace

25 minutes1 Credit

[](https://googlecloud.qwiklabs.com/focuses/128698/reviews?parent=classroom)

[

](https://googlecloud.qwiklabs.com/focuses/128698/reviews?parent=classroom)

## Overview

In this lab, you use Cloud Marketplace to quickly and easily deploy a LAMP stack on a Compute Engine instance. The Bitnami LAMP Stack provides a complete web development environment for Linux that can be launched in one click.ComponentRole

LinuxOperating system

Apache HTTP ServerWeb server

MySQLRelational database

PHPWeb application framework

phpMyAdminPHP administration tool

Learn more about the Bitnami LAMP stack from the Bitnami Documentation article [Google Cloud Platform](https://docs.bitnami.com/google/).

## Objectives

In this lab, you learn how to launch a solution using Cloud Marketplace.

## Task 1\. Sign in to the Google Cloud Platform (GCP) Console

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

## Task 2\. Use Cloud Marketplace to deploy a LAMP stack

1. In the GCP Console, on the Navigation menu (![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)), click Marketplace.
2. In the search bar, type `LAMP`.
3. In the search results, click LAMP Packaged by Bitnami.

If you choose another LAMP stack, such as the Google Click to Deploy offering, the lab instructions will not work as expected.
4. On the LAMP page, click Launch.

If this is your first time using Compute Engine, the Compute Engine API must be initialized before you can continue.
5. For Zone, select the deployment zone that Qwiklabs assigned to you.
6. Leave the remaining settings as their defaults.
7. If you are prompted to accept the GCP Marketplace Terms of Service, do so.
8. Click Deploy.
9. If a Welcome to Deployment Manager message appears, click Close to dismiss it.

The status of the deployment appears in the console window: lampstack-1 is being deployed. When the deployment of the infrastructure is complete, the status changes to lampstack-1 has been deployed.

After the software is installed, a summary of the details for the instance, including the site address, is displayed.

Click _Check my progress_ to verify the objective.

Use Cloud Marketplace to deploy a LAMP stack

## Task 3\. Verify your deployment

1. When the deployment is complete, click the Site address link in the right pane. (If the website is not responding, wait 30 seconds and try again.) If you see a redirection notice, click on that link to view your new site.

Alternatively, you can click Visit the site in the Get started with LAMP Packaged by Bitnami section of the page. A new browser tab displays a congratulations message. This page confirms that, as part of the LAMP stack, the Apache HTTP Server is running.
2. Close the congratulations browser tab.
3. On the GCP Console, under Get started with LAMP Packaged by Bitnami, click SSH.

In a new window, a secure login shell session on your virtual machine appears.
4. In the just-created SSH window, to change the current working directory to `/opt/bitnami`, execute the following command:

    cd /opt/bitnami

Copied!

5. To copy the `phpinfo.php` script from the installation directory to a publicly accessible location under the web server document root, execute the following command:

    sudo sh -c 'echo "<?php phpinfo(); ?>" > apache2/htdocs/phpinfo.php'

Copied!

The phpinfo.php script displays your PHP configuration. It is often used to verify a new PHP installation.
6. To close the SSH window, execute the following command:

    exit

Copied!

7. Open a new browser tab.
8. Type the following URL, and replace `SITE_ADDRESS` with the URL in the Site address field in the right pane of the lampstack page.

    http://SITE_ADDRESS/phpinfo.php

Copied!

A summary of the PHP configuration of your server is displayed.

Note: If you can't see the web page in the browser on your corporate laptop: If possible, exit any corporate VPN/network and try again. Enter the IP address on another device, such as a tablet or even a phone.

1. Close the phpinfo tab.

## Congratulations!

In this lab, you deployed a LAMP stack to a Compute Engine instance.

## End your lab

When you have completed your lab, click End Lab. Google Cloud Skills Boost removes the resources you've used and cleans the account for you.
