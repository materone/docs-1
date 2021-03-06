---
layout: page
title: Advanced configuration
description: Advanced configuration of the CoScale agent by using environment variables.
---

## Environment flags

Add these to `/etc/default/coscale-agent`

### `export COSCALE_DISABLE_AUTO_UPDATE=true`

Disable auto updating of the CoScale agent and plugins

### `export COSCALE_HOSTNAME=[custom hostname]`

By default the CoScale agent will use the system hostname and will not add a new server if the hostname already exists on our service. Change this value if you would like to set a custom hostname or to force adding a new server to the service.

Example: `export COSCALE_HOSTNAME=webserver`

### `export COSCALE_API_LOGLEVEL=debug`

Will output more information to logfiles, this should only be used for debugging purposes or when requested by CoScale support.
