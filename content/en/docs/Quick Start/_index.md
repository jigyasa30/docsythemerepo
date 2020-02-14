---
title: "Quick Start"
linkTitle: "Quick Start"
weight: 1
date: 2017-01-05
description: >
draft: false
---



Let’s walk through the end-to-end functionality of **AlertLens**.

#### Log in for the first time

1. Go to https://test1.alertlens.boltanalytics.com.

2. Login with the default credentials.

   You will be prompted to change the default password at first login.

3. Follow the online instructions and click the **Change Password** button.

   You will be redirected to the screen displaying the **Data Sources** pane.

#### Add Data Source

Let’s configure the data sources from which **AlertLens** gathers metrics for creating alerts. You can add freely available Grafana Wikimedia as a data source https://grafana.wikimedia.org:

4. Click the **Add** button next to the Grafana data source.

   A pop up appears.

5. Enter values to configure the data source and click the **Submit** button. Further, click the **Submit** button on the main screen.
<br>
![img](/grafana_data_source.JPG)<br>
​    A Data Source is configured.

#### Create Alert Conditions

Before creating a job, let’s walk through the steps required to create alert conditions.

6. Click the **Gearbox** icon in the top right corner, select **Alert** -> **Definitions** and click the **Add** button.

   The **Add Alert** pop up appears.

7. Setup **Warning** and **Critical** conditions.



   Let’s name it “Sharp Spike” to indicate that you want to get alert anytime a single anomalous point is detected.

   AlertLens scores each point on a scale of 0 to 100:

    - 0 means not anomalous
    - 100 means system extremely anomalous

    Let’s also give a metric threshold of 10 to suppress any low-value alerts.

    For example, a time-series may be around zero most of the times and you want to get alerted only when a much higher non-zero value occurs. Therefore, define the **Warning** threshold as when AlertLens score is above 50 and the **Critical** threshold when AlertLens score is above 70.

    ![img](/alert_definitions.PNG)



#### Add Job Using Grafana Add Job Flow

8. Open https://grafana.wikimedia.org/d/000000278/mysql-aggregated?orgId=1 in another browser tab.

    Let’s add the panel - **Rows read** in this dashboard as a job.

    ![img](/grafana_dashboard.PNG)

9. Click the **Configuration** tab and click the **New Job** button.

10. Select the **Grafana Easy Flow** workflow.

11. Select **Wikimedia** as the data source.

12. Select the**General** as the folder.

13. Select **MySQL Aggregated** as the dashboard.

14. Scroll in the **Panels** and select **Rows read.**

15. Enter the following values in the **Variables** text boxes:

     a.   **Datacenter**: eqiad prometheus/ops

     b.   **Group**: .*

     c.    **Shard**: .*

     d.   **Role**: .*

16. Select **Sharp Spike** as the alert.

17. Click **Submit**.

    The following screen appears.

    ![img](/job_summary.PNG)

18. Click **Save**. Congrats! The First job has been created.

    ![img](/job_created.PNG)

    Now, it will gather the data from **Data Source** and then perform **Training** and start **Inference**.  

#### Training and Inference



By default, the **Training** and **Inference** are turned off.

19. Go to the **Training** and **Inference** tabs and click the **Start All** button.

    By default, it goes back and gets 4 weeks of historical data (as shown in the **Scheduled for** column above). It should take about an hour. You can monitor the status in the **Summarizer** sub-tab. The whole process probably takes around an hour.

#### Alert Notifications

After Training and Inference has caught up to current time, walk through the steps to set **Alert Notifications**:

20. Go to **Dashboard** -> **Alert History** and see what Alerts have been triggered.

21. Click the **Gearbox** icon in the top right corner, select **Alert** -> **Notifications**.

    Let’s add a notification by **Email**.

22. Click the **Add** button and choose **Type** as **Email.**

    You can add your Gmail account as the sender and the recipient.

    **For Example**, check the following site for the settings: https://www.siteground.com/kb/google_free_smtp_server/



    ![img](/notification_email.PNG)

23. Click the **Test** button to make sure it works.

24. Now, go back to **Alert** -> **Definitions**. Edit the alert and enable the alerting method by choosing **Notification**  as **Email**.
