# Prometheus Stack on Kubernetes

This repository provides a guide and configuration files for installing and configuring the Prometheus monitoring stack on Kubernetes. The Prometheus stack includes Prometheus, Grafana, and various exporters for collecting and visualizing metrics from your Kubernetes cluster.

## Table of Contents
- [Introduction](#introduction)
- [Installation](#installation)
- [Configuration](#configuration)
- [Alerting](#alerting)
- [Additional Resources](#additional-resources)
- [Contributing](#contributing)
- [License](#license)

## Introduction
Prometheus is an open-source monitoring and alerting tool that is widely used in Kubernetes environments. It provides a flexible and scalable platform for collecting, analyzing, and alerting on metrics data. Grafana, on the other hand, is a visualization and analytics platform that works seamlessly with Prometheus to create interactive and customizable dashboards.

This repository aims to simplify the setup process of the Prometheus stack on Kubernetes by providing Helm charts and configuration files. It also includes guides and best practices for configuring and customizing the stack for your specific requirements.

## Installation
To install the Prometheus stack on your Kubernetes cluster, follow the steps in the [Installation Guide](./commands-prometheus.md). The guide provides detailed instructions on prerequisites, Helm chart installation, and namespace configuration.

## Configuration
Once you have installed the Prometheus stack, you can customize its configuration to suit your needs. In this example we have set up a Redis database and we aim to monitor it using helm charts. The [commands-redis](./commands-redis.md) covers various aspects of configuration, 

Refer to this guide to make the necessary configuration changes based on your specific monitoring requirements.

## Alerting
Alerting is a crucial component of any monitoring system. Prometheus supports powerful alerting capabilities that allow you to define alert rules, configure receivers, and manage alerting rules. The [alert rules file](./alert-rules.md) provides some examples for prometheus alerting system.

It covers topics such as defining alerting rules, using recording rules, configuring notification channels, and integrating with external services like PagerDuty or Slack.

## Additional Resources
- [Prometheus Documentation](https://prometheus.io/docs/)
- [Grafana Documentation](https://grafana.com/docs/)
- [Helm Documentation](https://helm.sh/docs/)
- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [Prometheus Community Helm Charts](https://github.com/prometheus-community/helm-charts)

These resources provide additional information and in-depth documentation on Prometheus, Grafana, Helm charts, and Kubernetes.

## Contributing
Contributions are welcome! If you have any ideas, suggestions, or improvements, feel free to open an issue or submit a pull request. 

