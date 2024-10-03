# Home Assistant 3D Printer Automations

This repository contains Home Assistant automations to detect when 3D prints have started and completed using OctoPrint.

## Automations

### Print Complete

This automation detects when a 3D print has completed in OctoPrint.

```yaml
alias: Print Complete
description: ""
trigger:
  - type: value
    platform: device
    device_id: xxx
    entity_id: xxx
    domain: sensor
    above: 99.99
    for:
      hours: 0
      minutes: 0
      seconds: 0
    below: 101
condition: []
action:
  - action: notify.xxx
    metadata: {}
    data:
      message: Print has completed!
      title: 3D Printer
  - action: notify.persistent_notification
    metadata: {}
    data:
      message: Print has completed!
      title: 3D Printer
mode: single
```

### Print Started

This automation sends an alert when OctoPrint has sent a message back to Home Assistant that a print has started.

```yaml
alias: Print Started
description: ""
trigger:
  - type: value
    platform: device
    device_id: xxx
    entity_id: xxx
    domain: sensor
    above: 0
    for:
      hours: 0
      minutes: 0
      seconds: 10
    below: 100
condition:
  - type: is_on
    condition: device
    device_id: xxx
    entity_id: xxx
    domain: binary_sensor
action:
  - action: notify.xxx
    metadata: {}
    data:
      message: Print has Started!
mode: single
```

## Setup

1. Ensure you have Home Assistant and OctoPrint set up and configured.
2. Replace `device_id`, `entity_id`, and `notify.xxx` with your actual device IDs and notification services.
3. Add the YAML automations to your Home Assistant configuration.
