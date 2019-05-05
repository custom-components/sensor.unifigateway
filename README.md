# sensor.unifigateway
High level health status of UniFi Security Gateway devices via UniFi Controller
  
[![Version](https://img.shields.io/badge/version-0.2.0-green.svg?style=for-the-badge)](#) [![mantained](https://img.shields.io/maintenance/yes/2019.svg?style=for-the-badge)](#) [![forum](https://img.shields.io/badge/forum-visit-orange.svg?style=for-the-badge)](https://community.home-assistant.io/t/unifi-security-gateway/71505)   

Connects to a Ubiquiti Controller instance to monitor high level health information on the setup including alerts and firmware updates

To get started download the files in
```
/custom_components/unifigateway/
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
### Configuration Variables

**username**

  (string)(Required) A user on the controller
  
**password**

(string)(Required) The password for the account
  
**host**

  (string)(Optional) The hostname or IP address of your controller
  Default value: localhost

**port**

  (integer)(Optional) The port of your controller's web interface
  Default value: 8443

**site_id**

  (string)(Optional) For multisite installations, you can specify site_id to specify which is used
  Default value: default

**verify_ssl**

  (boolean or filename)(Optional) Whether to do strict validation on SSL certificates of the Unifi controller. This can be true/false or the path to a locally trusted certificate to use for verification.
  Default value: false

**monitored_conditions**

  (list)(Optional) A list of the sensors to monitor
  Default value: If not defined all sensors are setup
  
### Monitored Conditions

The following sensors can be monitored

**vpn**

  The status of the VPN sub-system
  
**www**

  The status of the WWW sub-system
  Attribute data includes speedtest results
  
**lan**

  The status of the LAN sub-system
  Attribute data includes the IP of the USG
  
**wan**

  The status of the WAN sub-system
  Attribute data includes the WAN IP (e.g. dynamic IP as allocated by your ISP)
  
**wlan**

  The status of the Wifi Access Points
  Attribute data includes number of guests
  
**alerts**

  The number of unarchived alerts on the controller
  Attribute data lists the detail of each alert
  
**firmware**

  The number of devices that are available for a firmware update.
  Attribute data lists the friendly name of the relvant devices.
  
### In Development - Notes

The sensor currently accesses the controller everytime an individual sensor is updated. This should be optimised to access once and then feed data to the other appropriate sensors to reduce overhead.
