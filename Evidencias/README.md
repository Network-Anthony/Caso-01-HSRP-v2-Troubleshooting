# Validation Evidence

This directory contains the validation evidence collected during the implementation and validation of HSRP version 2.

## Objective

The purpose of these screenshots is to verify that the HSRP configuration is working correctly before performing the failover test.

## Evidence

| File | Description |
|------|-------------|
| 01_R2_Active_Show_Standby_Brief.png | Confirms that R2 is operating as the Active router. |
| 02_R3_Standby_Show_Standby_Brief.png | Confirms that R3 is operating as the Standby router. |
| 03_Ping_Virtual_IP.png | Verifies successful connectivity to the HSRP virtual IP address. |
| 04_Ping_Loopback.png | Verifies end-to-end connectivity to the simulated Internet loopback. |
| 05_Trace_Loopback.png | Shows the forwarding path before the failover scenario. |
