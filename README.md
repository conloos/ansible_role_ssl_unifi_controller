# Ansible Role for configure unifi-controller

**summary**
This role is for configuring a unifi-controller. 
Look in the tasks directory for each configuration.
All configurations are held atomically via their own files. 

## Variables that have to be defined

| variable | description |
| -------- | ----------- |
|||

## flow diagram

```
----------------------------------------
| unifi-regenerate-certificate.service |      Systemd start service to regenerate the certificate if needed
----------------------------------------
      |
      |
      |
      V
--------------------------------------
| unifi-regenerate-certificate.sh |        renew or regenerate certificate
--------------------------------------
      |
      | regenerate at startup or 1/3 certificate lifetime
      |
      V
-------------------------------
| unifi-rebuild-keystore.path |               Monitors the certificate for changes
-------------------------------
      |
      |
      |
      V
----------------------------------
| unifi-rebuild-keystore.service |            Called by unifi-rebuild-keystore.path
----------------------------------
      |
      |
      |
      V
--------------------------------
| unifi-rebuild-keystore.sh |              Regenerates the keystore and restart unifi.service
--------------------------------
```