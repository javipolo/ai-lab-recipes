# Amazon Web Services modifications for RHEL AI
Trying to mimic as much as possible the [changes on RHEL for AWS](https://github.com/osbuild/images/blob/main/pkg/distro/rhel/rhel9/aws.go)

## Changes

- Extra kernel parameters

```
console=ttyS0,115200n8 net.ifnames=0 nvme_core.io_timeout=4294967295
```

- Timezone: UTC
- Chrony configuration:
    - Change server
    - LeapsecTz
- Locale: en_US.UTF-8
- Keymap: us
- X11 layout: us

- Getty configuration
    - NautoVTs false

- Cloud init default user: `ec2-user`

- Packages
    - @core metapackage
    - authselect-compat
    - langpacks-en
    - tuned

- Services
    - nm-cloud-setup.service
    - nm-cloud-setup.timer
    - tuned

## Things we are not changing, despite being in RHEL for AWS

  - Packages
    - authselect-compat
    - @core
    - dracut-config-generic
    - rh-amazon-rhui-client
    - yum-utils

- Network configuration
    - IPV6 false

