# Day 02: Client DNS Configuration

## Goal
Switch `srv1` and `Client` from using local `/etc/hosts` files to using the centralized DNS server on `srv2`.

## Configuration
### srv1 (Netplan)
Updated `/etc/netplan/50-cloud-init.yaml` to force `enp0s8` to use `192.168.56.11`.
```yaml
nameservers:
    addresses: [192.168.56.11, 1.1.1.1]
