---
title: UPS Sensor
description: "Instructions on how to set up UPS sensors within Home Assistant."
logo: ups.png
ha_category:
  - Postal Service
ha_release: 0.39
ha_iot_class: Cloud Polling
redirect_from:
 - /components/sensor.ups/
---

<div class="note warning">

This integration is deprecated and will be removed in Home Assistant 0.100.0.

For more information see [Architecture Decision Record: 0004](https://github.com/home-assistant/architecture/blob/master/adr/0004-webscraping.md).

</div>

The `ups` platform allows one to track deliveries by the [UPS](https://www.ups.com/). To use this sensor, you need a [My UPS Account](https://www.ups.com/mychoice).

## Configuration

To enable this sensor, add the following lines to your `configuration.yaml`:

```yaml
# Example configuration.yaml entry
sensor:
  - platform: ups
    username: YOUR_USERNAME
    password: YOUR_PASSWORD
```

Configuration options for the UPS Sensor:

- **username** (*Required*): The username to access the UPS My Choice service.
- **password** (*Required*): The password for the given username.
- **name** (*Optional*): Name the sensor.
- **scan_inverval** (*Optional*): Minimum time interval between updates. Default is 1 hour. Supported formats:
  - `scan_interval: 'HH:MM:SS'`
  - `scan_interval: 'HH:MM'`
  - Time period dictionary, e.g.:
    <pre>scan_interval:
        # At least one of these must be specified:
        days: 0
        hours: 0
        minutes: 3
        seconds: 30
        milliseconds: 0
    </pre>

<div class='note warning'>
The UPS sensor logs into the UPS My Choice website to scrape package data. It does not use an API. Use at your own risk.
</div>

<div class='note info'>
If the UPS sensor is throwing an error about not being able to login to the UPS My Choice website, it's likely because there is a new UPS Technology Agreement (UTA) preventing the scraper from accessing the package data. Login to UPS My Choice manually and accept the UTA to resolve this.
</div>
