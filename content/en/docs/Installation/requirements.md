---
title: "Requirements"
date: 2019-11-29T22:53:54+05:30
draft: false
---



This page includes useful information on the supported Operating Systems as well as the hardware requirements that are needed to install and use Grafana.

## Supported operating systems

The following operating systems are supported for Grafana installation:

- [Debian / Ubuntu](https://grafana.com/docs/installation/debian)
- [RPM-based Linux (CentOS, Fedora, OpenSuse, RedHat)](https://grafana.com/docs/installation/rpm)
- [macOS](https://grafana.com/docs/installation/mac)
- [Windows](https://grafana.com/docs/installation/windows)

## Unsupported operating systems

Installation of Grafana on other operating systems is possible, but not supported. Please see the [building from source](https://grafana.com/docs/project/building_from_source/#building-grafana-from-source) guide for more information.

## Hardware requirements

Grafana does not use a lot of resources and is very lightweight in use of memory and CPU. Minimum recommendation is 255mb of memory and 1 CPU.

Depending on what features are being used and to what extent the requirements varies. Features that consume and requires more resources:

- Server side rendering of images
- [Alerting](https://grafana.com/docs/alerting/rules/)
- Data source proxy

## Database

Grafana requires a database to store its configuration data, e.g. users, data sources and dashboards. The exact requirements depend on the size of the Grafana installation (e.g. the number of users, data sources, dashboards, features in use etc).

Grafana supports the following databases:

- SQLite
- MySQL
- PostgreSQL

Per default Grafana ships with and uses SQLite, which is an embedded database stored on disk in Grafana’s installation location.

## Supported web browsers

Grafana is supported in the current version of the following browsers. Older versions of these browsers might not be supported, so you should always upgrade to the latest version when using Grafana.

- Chrome/Chromium
- Firefox
- Safari
- Microsoft Edge
- Internet Explorer 11 is only fully supported in Grafana versions prior v6.0.

> Note: Always enable JavaScript in your browser. Running Grafana without JavaScript enabled in the browser is not supported.
