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

---

# Troubleshooting Evidence

The following screenshots document the failover process and the behavior of HSRP version 2 when preempt is not configured.

| File | Description |
|------|-------------|
| 06_R2_Active_Before_Failure.png | Initial state showing R2 operating as the Active router before the simulated failure. |
| 07_R3_Standby_Before_Failure.png | Initial state showing R3 operating as the Standby router. |
| 08_R3_Active_After_Failover.png | R3 assumes the Active role after R2 becomes unavailable. |
| 09_Ping_Continuity_During_Failover.png | Continuous ping demonstrating temporary packet loss and service recovery during failover. |
| 10_R2_Standby_After_Recovery.png | After R2 recovers, it remains in the Standby state despite having higher priority. |
| 11_R3_Remains_Active.png | R3 continues operating as the Active router because preempt has not been configured. |


## Solution Validation (Preempt Enabled)

| File | Description |
|------|-------------|
| 12_Preempt_Configuration.png | HSRP configuration showing the `standby 10 preempt` command enabled on R2. |
| 13_R3_Active_During_Failover.png | R3 becomes the Active router after the failure of R2. |
| 14_R2_Reclaims_Active.png | R2 automatically regains the Active role after recovering. |
| 15_R3_Returns_To_Standby.png | R3 returns to the Standby state after R2 resumes the Active role. |


## Summary

This evidence documents the complete lifecycle of the HSRP v2 troubleshooting case study, including the initial deployment, failover validation, root cause identification, and verification of the implemented solution using the **preempt** feature.

The collected screenshots demonstrate both the problem scenario and the successful resolution, providing a complete technical record of the troubleshooting process.
