
---
title: "Documentation"
linkTitle: "Documentation"
weight: 30
menu:
  main:
    weight: 30
---

{{% pageinfo %}}
This is a placeholder page that shows you how to use this template site.
{{% /pageinfo %}}


TThis guide will help you get started and acquainted with Grafana. It assumes you have a working Grafana server up and running. If not please read the [installation guide](https://grafana.com/docs/installation/).

## Logging in for the first time

To run Grafana open your browser and go to http://localhost:3000/. 3000 is the default HTTP port that Grafana listens to if you haven’t [configured a different port](https://grafana.com/docs/installation/configuration/#http-port).

There you will see the login page. Default username is admin and default password is admin. When you log in for the first time you will be asked to change your password. We strongly encourage you to follow Grafana’s best practices and change the default administrator password. You can later go to user preferences and change your user name.

## How to add a data source


Before you create your first dashboard you need to add your data source.

First move your cursor to the cog on the side menu which will show you the configuration menu. If the side menu is not visible click the Grafana icon in the upper left corner. The first item on the configuration menu is data sources, click on that and you’ll be taken to the data sources page where you can add and edit data sources. You can also simply click the cog.

Click Add data source and you will come to the settings page of your new data source.



First, give the data source a Name and then select which Type of data source you’ll want to create, see [Supported data sources]



After you have configured your data source you are ready to save and test.

## Beginner guides

Watch the 10min [beginners guide to building dashboards](https://www.youtube.com/watch?v=sKNZMtoSHN4&index=7&list=PLDGkOdUX1Ujo3wHw9-z5Vo12YLqXRjzg2) to get a quick intro to setting up Dashboards and Panels.

## Basic concepts

Read the [Basic Concepts](https://grafana.com/docs/guides/basic_concepts) document to get a crash course in key Grafana concepts.

### Top header

Let’s start with creating a new Dashboard. You can find the new Dashboard link on the right side of the Dashboard picker. You now have a blank Dashboard.
