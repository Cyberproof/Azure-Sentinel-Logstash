# Logstash Syslog CEF config file

## Purpose

This conf file will receive syslog CEF events and will push them to Log analytics.

```CONF
input {
  tcp {
    port => 514
    type => syslog
    codec => cef
  }
}
filter {
  metrics {
    meter => "events"
    add_tag => "metric"
  }
}
output {
  if "metric" in [tags] {
    stdout {
      codec => line {
        format => "rate: %{[events][rate_1m]}"
      }
    }
  }
  else {
    azure_loganalytics {
      customer_id => "WorkSpace.ID"
      shared_key => "Workspace.Key"
      log_type => "CustomTableName"
      time_generated_field => "iso8610timestamp"
      key_names => []
      key_types => {}
    }
  }
}
```
