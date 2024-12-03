---
title: "Web Cloud Databases - How to manage logs"
excerpt: "Find out how to manage the logs for your databases hosted on your Web Cloud Databases server"
updated: 2024-11-25
---

## Objective

A log is an event that occurs on a computer system (server, computer, application, website, database, computer network, etc.).  
For example, a log might record and contain one or more of the following:

- The timestamp (date, time, minute, second, etc.) of the event.
- The nature of the event (connection, disconnection, error, download, upload, alert, etc.).
- Additional information on the event (page or file accessed, application launched, remote server called, name of a file loaded or downloaded, etc.)
- The origin of the event (user ID, source IP address, source program, etc.).
- The state of the system where the event occurs (available resources, remaining memory, CPU usage, etc.).

Most of the time, the logs are generated directly by the IT systems where the events take place.  
They are stored in text files, also called log files.

As a result, log files allow you to:

- Analyze the behaviour of the IT system generating logs.
- Identify errors that have occurred on the computer system.
- Resolve errors encountered on the computer system.
- Optimize and improve the performance of the IT system.

Your [Web Cloud Databases](/links/web/databases) solution generates its own logs.

In some situations, you may need to retrieve the logs:

- For your Web Cloud Databases server.
- For one of the databases hosted on your Web Cloud Databases server.

**Find out how to view and manage logs for your Web Cloud Databases solution.**

## Requirements

- A [Web Cloud Databases](/links/web/databases) solution
- Access to the [OVHcloud Control Panel](/links/manager)

## Instructions

> [!warning]
>
> This guide is designed to help you with common tasks. Nevertheless, we recommend contacting a [specialist service provider](/links/partner) if you encounter any difficulties. We will not be able to provide you with interpretation assistance for the logs available with your Web Cloud Databases solution. You can find more information in the [Go further](#go-further) section of this guide.
>

### View logs in real time for your Web Cloud Databases

To check the logs for your Web Cloud Databases solution in real time, perform the following actions:

1. Log in to your [OVHcloud Control Panel](/links/manager).
2. In the top menu of the Control Panel, click on the `Web Cloud`{.action} tab.
3. In the left-hand column, click on the `Web Cloud Databases`{.action} dropdown menu.
4. Select the Web Cloud Database instance concerned.
5. On the page that appears, click on the `Logs`{.action} tab.

![Web Cloud Databases](/pages/assets/screens/control_panel/product-selection/web-cloud/web-cloud-databases/logs/tab.png){.thumbnail}

This integrated console provides you with real-time logs for your Web Cloud Databases solution.

> [!primary]
>
> Since the logs are only available in real time, they are only generated and displayed while the `Logs`{.action} tab is open.
>
> If you leave the `Logs`{.action} tab and come back to it later, the log history that was previously displayed will be gone.
>

### Retrieve the log history of your Web Cloud Databases solution

To retrieve the log history of your Web Cloud Databases solution, you will need to log in via SFTP.

> [!warning]
>
> Before you log in, check that the public IP address of the workstation you are using is authorized on your Web Cloud Databases server with the `SFTP` option.
>
> To check this, retrieve the public IP address of your internet access point and refer to the **Authorize an IP address** section of [this guide](/pages/web_cloud/web_cloud_databases/starting_with_clouddb).
>

To retrieve the SFTP connection information for your Web Cloud Databases solution, perform the following actions:

1. Log in to your [OVHcloud Control Panel](/links/manager).
2. In the top menu of the Control Panel, click on the `Web Cloud`{.action} tab.
3. In the left-hand column, click on the `Web Cloud Databases`{.action} dropdown menu.
4. Select the Web Cloud Databases solution concerned.
5. In the `General information`{.action} tab you can find a box labeled `Login information`{.action}.
6. Below `SFTP`{.action}, you will find all the information you need to log in via SFTP.

> [!primary]
>
> If you do not know the `Server password`, click the `...`{.action} button on the right to modify it.
>

![Web Cloud Databases](/pages/assets/screens/control_panel/product-selection/web-cloud/web-cloud-databases/general-information/sftp-login.png){.thumbnail}

Once you have retrieved the SFTP login credentials, log in via an FTP client (FileZilla, Cyberduck, WinSCP, etc.).

For FileZilla, go to the top left in the `File`{.action} menu, then click `Site Manager`{.action}.

Click `New site`{.action}, then enter the settings listed above.

![Web Cloud Databases](/pages/assets/screens/other/web-tools/filezilla/site-manager.png){.thumbnail}

The log file `stdout.log` is located at the root.

You can download it to your desktop to view it.

> [!primary]
>
> An additional log file named `slow-query.log` may appear in the SFTP root of your Cloud Databases Web server.  
> This file contains the history of slow requests that have run on your Web Cloud Databases server. 
> 
> By default, the value is set to 1 second on Web Cloud Databases solutions in the **long_query_time** variable.
> 
> With this file, you can optimize your scripts and the content of your databases to improve the performance of your associated services.
>

### Subscribe to Logs Data Platform logs from your Web Cloud Databases solution <a name="wcdb-ldp"></a>

[Logs Data Platform](/links/manage-operate/ldp) is a platform for managing your logs. It can be useful if you have a very large infrastructure, or if your services generate a lot of logs. This platform is designed to facilitate log aggregation and management.

It works by retrieving logs generated by your infrastructure, websites or applications, for example:

- To store them.
- To display them in dashboards in real time.
- To allow users to perform complex queries.
- To filter them by date, application, type or content.

For more information on the Logs Data Platform, please refer to our [Introduction to the Logs Data Platform](/pages/manage_and_operate/observability/logs_data_platform/getting_started_introduction_to_LDP) (EN).

Since [Web Cloud Databases](/links/web/databases) solutions can be used with a wide range of services (web hosting, VPS, dedicated servers, etc.), these can be subscribed to Logs Data Platform via data stream, in addition to the real-time logs already available.

To subscribe your Web Cloud Databases solution to a data stream on the Logs Data Platform, perform the following actions:

1. Log in to your [OVHcloud Control Panel](/links/manager).
2. On the line at the top of the Control Panel, click on the `Web Cloud`{.action} tab.
3. In the left-hand column, click on the `Web Cloud Databases`{.action} dropdown menu.
4. Select the Web Cloud Databases instance concerned.
5. On the page that appears, click on the `Logs`{.action} tab.
6. To the right of the box where your logs are displayed in real time, click the `Subscribe`{.action} button.

![Web Cloud Databases](/pages/assets/screens/control_panel/product-selection/web-cloud/web-cloud-databases/logs/tab-subscribe.png){.thumbnail}

In the new page that opens, if you have several Logs Data Platform solutions in your [OVHcloud Control Panel](/links/manager), select the Logs Data Platform reference you would like to subscribe to from the dropdown list just below the `Add data stream` button.

![Web Cloud Databases](/pages/assets/screens/control_panel/product-selection/web-cloud/web-cloud-databases/logs/data-stream.png){.thumbnail}

There are two scenarios for subscribing to your Web Cloud Databases solution.

#### Case 1 - Subscribe to an existing feed on your Logs Data Platform <a name="wcdb-ldp-case1"></a>

If the data stream already exists, it will appear as a row in the table at the bottom of the page.  
In this specific case, to subscribe your Web Cloud Databases solution to this existing stream, simply click the `Subscribe`{.action} button to the right of the line corresponding to the stream concerned. 

After a few seconds, if you stay on the same page, a message will appear in your Control Panel to inform you that the subscription has been created.

#### Case 2 - Subscribe to a new data stream on your Logs Data Platform

If the data stream concerned does not yet exist, click the `Add data stream`{.action} button.  
You will then be redirected to a new page in the OVHcloud Control Panel, where you can create and add a new data stream on your Logs Data Platform solution.

![Web Cloud Databases](/pages/assets/screens/control_panel/product-selection/bare-metal-cloud/logs-data-platform/data-stream/add-data-stream.png){.thumbnail}

If necessary, please refer to our guides “[Introduction to Logs Data Platform](/pages/manage_and_operate/observability/logs_data_platform/getting_started_introduction_to_LDP)” (EN) and “[Getting started quickly with Logs Data Platform](/pages/manage_and_operate/observability/logs_data_platform/getting_started_quick_start)” (EN) to carry out these actions.

Once you have filled in the various forms, click the `Save`{.action} button.

You will then be redirected to the `Data stream` tab of your Logs Data Platform solution.

Now you just need to subscribe your Web Cloud Databases solution to your newly created stream on your Logs Data Platform solution.

To do this, and as explained [previously](#wcdb-ldp), go back to the `Logs`{.action} tab of your Web Cloud Databases solution to subscribe to this new data stream, then follow [Case 1](#wcdb-ldp-case1) described above.

## Go further <a name="go-further"></a>

[Getting started with your Web Cloud Databases](/pages/web_cloud/web_cloud_databases/starting_with_clouddb)

[Introduction to Logs Data Platform](/pages/manage_and_operate/observability/logs_data_platform/getting_started_introduction_to_LDP)

[Getting started quickly with Logs Data Platform](/pages/manage_and_operate/observability/logs_data_platform/getting_started_quick_start)
 
For specialized services (SEO, development, etc.), contact [OVHcloud partners](/links/partner).
  
Join our [community of users](/links/community).