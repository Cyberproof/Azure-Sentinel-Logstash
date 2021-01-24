# Azure-Sentinel-Logstash

A containerized Logstash ready to send data to Log Analytics or Event Hub.

## How to install

In order to install the image:

```Bash
docker pull saggiehaim/logstash-la:7.10.1
```

## How to run

To run a Logstash instance with your config file:

```Bash
docker run --rm -it -v ~/logstashconf/logstash.conf:/usr/share/logstash/config/logstash.conf saggiehaim/logstash-la:7.10.1
```