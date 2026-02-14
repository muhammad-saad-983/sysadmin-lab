# Day 01: Centralized DNS setup with dnsmasq

## Goal
Install and Configure `dnsmasq` on `srv2` to act as local DNS resolver.

## Configuration Details (`/etc/dnsmasq.d/lab.conf`)
- **Upstream Resolvers:** `1.1.1.1` and `8.8.8.8`.
- **Local Enteries:**
  - `site1.lab` -> `192.168.56.10`
  - `site2.lab` -> `192.168.56.10`
  - `srv1.lab` -> `192.168.56.10`
  - `srv2.lab` -> `192.168.56.11`

## Verification
1. **Service Status:** `dnsmasq` is active and enabled.
2. **Network Check:** `ss -tulpn | grep :53` confirms the service is listening on the standard DNS port.
3. **Resolution Test:** `dig @127.0.0.1 site1.lab +short` returns `192.168.56.10`.

## Why Dnsmasq?
It is lightweight and easy to configure. For a small lab env, it is much faster to set up than a full BIND server while providing the same essential functionality.
