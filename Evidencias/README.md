# Validation Evidence

This directory contains the validation evidence collected after implementing HSRP version 2.

## Objectives

The purpose of these screenshots is to verify:

- Active and Standby roles.
- Virtual gateway availability.
- End-to-end connectivity.
- Traffic path before the failover scenario.

## Evidence List

| File | Description |
|------|-------------|
| 01_R2_Active_State.png | R2 operating as the Active HSRP router. |
| 02_R3_Standby_State.png | R3 operating as the Standby HSRP router. |
| 03_Ping_Virtual_IP.png | Successful ping to the HSRP virtual IP address. |
| 04_Ping_Loopback.png | Successful connectivity to the Internet simulated Loopback interface. |
| 05_Trace_Loopback.png | Trace showing the forwarding path before failover testing. |
