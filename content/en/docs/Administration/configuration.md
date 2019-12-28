---
title: "Configuration"
date: 2019-11-29T22:46:25+05:30
draft: false
---

The Grafana back-end has a number of configuration options that can be specified in a `.ini` configuration file or specified using environment variables.

> **Note.** Grafana needs to be restarted for any configuration changes to take effect.

## Comments in .ini Files

Semicolons (the `;` char) are the standard way to comment out lines in a `.ini` file.

A common problem is forgetting to uncomment a line in the `custom.ini` (or `grafana.ini`) file which causes the configuration option to be ignored.

## Config file locations

- Default configuration from `$WORKING_DIR/conf/defaults.ini`
- Custom configuration from `$WORKING_DIR/conf/custom.ini`
- The custom configuration file path can be overridden using the `--config` parameter

> **Note.** If you have installed Grafana using the `deb` or `rpm` packages, then your configuration file is located at `/etc/grafana/grafana.ini` and a separate `custom.ini` is not used. This path is specified in the Grafana init.d script using `--config` file parameter.

**macOS:** By default, the configuration file is located at `/usr/local/etc/grafana/grafana.ini`.

## Using environment variables

All options in the configuration file (listed below) can be overridden using environment variables using the syntax:

```bash
GF_<SectionName>_<KeyName>
```

Where the section name is the text within the brackets. Everything should be upper case, `.` should be replaced by `_`. For example, given these configuration settings:

```bash
# default section
instance_name = ${HOSTNAME}

[security]
admin_user = admin

[auth.google]
client_secret = 0ldS3cretKey
```

Then you can override them using:

```bash
export GF_DEFAULT_INSTANCE_NAME=my-instance
export GF_SECURITY_ADMIN_USER=true
export GF_AUTH_GOOGLE_CLIENT_SECRET=newS3cretKey
```
