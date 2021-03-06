---
layout: page
title: Docker plugin
description: Information on how to install the docker plugin and configure your container monitoring
---

> Docker is the world’s leading software containerization platform. Docker is an open platform for developers and sysadmins to build, ship, and run distributed applications, whether on laptops, data center VMs, or the cloud. Docker containers wrap a piece of software in a complete filesystem that contains everything needed to run: code, runtime, system tools, system libraries – anything that can be installed on a server. This guarantees that the software will always run the same, regardless of its environment.

More information on: [https://www.docker.com/](https://www.docker.com/)

## Events

* Events reported by Docker
    * Container created
    * Container started
    * Container stopped
    * Container died
    * Container destroyed
    * Container killed
    * Container attach
* Events generated when 'docker exec' is called
    * Creating a plugin inside a container
    * Starting a plugin inside a container
    * Command was ran inside a container
* Docker service state watcher

## Metrics

| Metric name                                             | Metric unit |
|---------------------------------------------------------|-------------|
| Docker running                                          | %           |
| Docker container total cpu usage                        | %           |
| Docker container user mode cpu usage                    | %           |
| Docker container kernel mode cpu usage                  | %           |
| Docker container network receive errors total           | #           |
| Docker container network transmit errors total          | #           |
| Docker container network receive packets dropped total  | #           |
| Docker container network transmit packets dropped total | #           |
| Docker container memory usage bytes                     | b           |
| Docker container memory limit                           | b           |
| Docker container network receive rate                   | b/s         |
| Docker container network transmit rate                  | b/s         |
| Docker container block IO read rate                     | b/s         |
| Docker container block IO write rate                    | b/s         |


## How it works
The CoScale agent detects running containers on your system. With minimal configuration, it will start the required plugins whenever a running container is detected. These plugins will start within the same namespace as the container, so there is no need to forward ports or mount logfiles to your local filesystem. When a container disappears, the plugin will also automatically stop. Our plugins will do all their work from inside the container and send the data to our agent that will send it through to our platform.

## Installation

### Configure the CoScale agent with the Docker plugin

Choose the Docker plugin from our plugin list. Next, for each Docker image that you would like to monitor, you need to add a set of plugins to be installed when the image is run. Version is the same as the docker tag, so you can use `latest` or any custom tags you prefer. After adding a plugin, you will receive instructions on how to setup your Docker container so that our agent can monitor it.

<img src="{{ site.baseurl}}/gfx/agent/plugins/docker/configuration.png" alt="Screenshot of Docker configuration" class="img-responsive" />

#### Configurations

CoScale provides some custom images for the services that require configuration. Some of our plugins will work outside of the box without any configuration.

<table>
    <tr>
        <th>No configuration required</th>
        <th>Some setup required (custom image available*)</th>
        <th>Custom image coming soon</th>
    </tr>
    <tr>
        <td>
            <ul>
                <li>Redis</li>
                <li>MongoDB</li>
                <li>Memcached</li>
            </ul>
        </td>
        <td>
            <ul>
                <li>Nginx</li>
                <li>RabbitMQ</li>
                <li>MySQL</li>
            </ul>
        </td>
        <td>
            <ul>
                <li>Postgres</li>
                <li>Elasticsearch</li>
                <li>Tomcat</li>
                <li>Haproxy</li>
                <li>MariaDB</li>
                <li>Cassandra</li>
                <li>Sentry</li>
            </ul>
        </td>
    </tr>
</table>

*You can find a list of custom Docker images on [Docker Hub](https://hub.docker.com/u/coscale/).


### Install the CoScale agent on your machine running the Docker containers.

Follow the instructions in our application to install the CoScale agent on your Docker host. Our agent will then start the necessary plugins for the containers running on the Docker host. There is no need to restart or reconfigure the agent when containers are removed or restarted. Our agent will handle the plugins for monitoring the containers without manual intervention.

### Our agent will now collect data

Inside your dashboard under `Servers` you will now get a list of your running containers. All other metrics will be available under the usual metric groups.
