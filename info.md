# sensor.unifigateway
High level health status of UniFi Security Gateway devices via UniFi Controller

Connects to a Ubiquiti Controller instance to monitor high level health information on the setup including alerts and firmware updates

To get started download
```
/custom_components/unifigateway/manifest.json
/custom_components/unifigateway/__init__.py
/custom_components/unifigateway/sensor.py
```
into
```
<config directory>/custom_components/unifigateway/
```

**Example configuration.yaml:**

```yaml
# Example configuration.yaml entry
sensor:
  - platform: unifigateway
    host: unifi
    username: username
    password: password
    monitored_conditions:
      - www
      - wlan
      - alerts
      - firmware
```
