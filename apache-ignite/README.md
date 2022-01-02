# Apache Ignite Grafana dashboard

This directory includes the custom Grafana dashboard for Apache Ignite. The current implementation is primarily suitable for Kubernetes, but you can easily adapt it for any environment.

## Configurations

The [prom_config.yml](prom_config.yml) and [vmservice_scrape.yml](kubernetes/vmservice_scrape.yml) files include the basic scrapers settings that need to be made. You can use **either of them**. Special attention should be paid to `metricRelabelConfigs`, because it converts a set of metrics of the same type into a single metric for easy visualization in Grafana.

### No Kubernetes settings
1. File [prom_config.yml](prom_config.yml) is an example variant of how the config should look for installing Prometheus without Kubernetes. Additional settings may be needed here.

### Only Kubernetes settings
1. On our project we used Kubernetes + Victoria Metrics, so 100% working config is [vmservice_scrape.yml](kubernetes/vmservice_scrape.yml).
2. [endpoints.yml](kubernetes/endpoints.yml) and [service.yml](kubernetes/service.yml) files contain the settings needed to collect promrtheus metrics from external (outside Kubernetes) sources.

### Common configs

1. [build.gradle](build.gradle) - extra dependencies for Prometheus metrics
2. [config.xml](config.xml) - extra beans into your Apache Ignite configuration file

## Grafana Dashboard

The file [ignite_dashboard.json](ignite_dashboard.json) contains the actual Grafana dashboard for Apache Ignite. You can simply import it into your Grafana.

![1](assets/1.png?raw=true)

![2](assets/2.png?raw=true)

![3](assets/3.png?raw=true)