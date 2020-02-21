---
title: "Quick Start"
linkTitle: "Quick Start"
weight: 1
date: 2017-01-05
description: >
draft: false
---

Let’s walk through the end-to-end functionality of **AlertLens**.
### Step 1: Log in for the first time

1. Go to the **AlertLens URL** provided to you.

2. Log in with the default credentials which are provided to you.

   You will be prompted to change the default password at first login.

3. Follow the online instructions and click the **Change Password** button.

   You will be redirected to the screen displaying the list of **Data Sources**.

### Step 2: Add Data Source

Let’s configure the data sources from which **AlertLens** gathers metrics for creating alerts. As an example for the quick start, let's add a panel from one of the Grafana (open source) dashboards at https://grafana.wikimedia.org.

1. Click the **Add** button next to the Grafana data source.

   A pop up appears.

2. Enter values to configure the data source and click the **Submit** button. Further, click the **Submit** button on the main screen.
<br>
![img](/grafana_data_source.JPG)<br>
​<br>
A **Data Source** is configured.

### Step 3: Create Alert Conditions

Before creating a job, perform the following steps required to create alert conditions:

1. Click the **Gearbox** icon ![img](/gearbox.JPG) in the top right corner of the screen, select **Alert** -> **Definitions** and click the **Add** button.

    The **Add Alert** pop up appears.

2. Setup **Warning** and **Critical** conditions.

   Let’s name it “**Sharp Spike**” to indicate that you want to get alert anytime a single anomalous point is detected.

    AlertLens scores each point on a scale of 0 to 100:

      - 0 means not anomalous
      - 100 means system is extremely anomalous

      Let’s also give a metric threshold of 10 to suppress any low-value alerts.

      For example, a time-series may be around zero most of the times and you want to get alerted only when a much higher non-zero value occurs. Therefore, define the **Warning** threshold as when AlertLens score is above 50 and the **Critical** threshold when AlertLens score is above 70.

      ![img](/alert_definitions.PNG)

3. Click the **Submit** button and **Alert Condition** is created.

### Step 4: Add Job Using Grafana Add Job Flow

1. Open https://grafana.wikimedia.org/d/000000278/mysql-aggregated?orgId=1 in another browser tab.

    Let’s add the panel - **Rows read** in this dashboard as a job.

    ![img](/grafana_dashboard.PNG)

2. Click the **Configuration** tab and click the **New Job** button.

3. Select the **Grafana Easy Flow** workflow.

4. Select **Wikimedia** as the data source.

5. Select **General** as the folder.

6. Select **MySQL Aggregated** as the dashboard.

7. Scroll in the **Panels** and select **Rows read.**

8. Enter the following values in the **Variables** text boxes:

    -   **Datacenter**: eqiad prometheus/ops

    -   **Group**: .*

    -    **Shard**: .*

    -   **Role**: .*

9. Select **Sharp Spike** as the alert.

10. Click the **Submit** button.

    The following screen appears.

    ![img](/job_summary.PNG)

11. Click **Save**. Congrats! The First **Job** has been created.

    ![img](/job_created.PNG)

    Now, it will gather data from the **Data Source** and then perform **Training** and start **Inference**.  

### Step 5: Training and Inference

By default, the **Training** and **Inference** are turned off.

- Go to the **Training** and **Inference** tabs and click the **Start All** button.

    By default, it goes back and gets 4 weeks of historical data (as shown in the **Scheduled for** column above). It takes about an hour. You can monitor the status in the **Summarizer** sub-tab. The whole process probably takes around an hour.

### Step 6: Alert Notifications
After Training and Inference has caught up to the current time, perform the following steps to set [**Alert Notifications**](/docs/settings/alert-notifications/):

1. Go to [**Dashboard**](/docs/dashboard/) -> [**Alert History**](/docs/dashboard/alerts_history/) and see what Alerts have been triggered.

2. Click the **Gearbox** icon ![img](/gearbox.JPG) in the top right corner of the screen, select **Alert** -> **Notifications**.

    Let’s add a notification by **Email**.

3. Click the **Add** button and choose **Type** as **Email** and enter all the email credentials. For configuration settings, refer section
[Email Settings](/docs/settings/alert-notifications/email/).

    ![img](/notification_email.PNG)

4. Click the **Test** button to make sure it works.

5. Now, go back to **Alert** -> **Definitions**. Edit (![img](/edit.JPG)) the definition to enable the alerting method and choose [**Email**](/docs/settings/alert-notifications/email/) as **Notification**.
