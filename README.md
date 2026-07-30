# Caso-01-HSRP-v2-Troubleshooting

## Overview

This repository documents the complete development of an HSRP Version 2 troubleshooting lab built in GNS3.

The main goal of this project was not only to configure HSRP, but also to understand how the protocol behaves during a failover scenario. After completing the initial configuration, a network failure was simulated by disconnecting the Active router from the LAN. As expected, the Standby router took over the Active role and network connectivity was maintained through the virtual IP address.

Once the failed router came back online, an unexpected behavior was observed: despite having the highest priority, it did not recover the Active role. Instead of applying a solution immediately, the behavior was analyzed to understand why it occurred.

After identifying that the `preempt` feature had not been configured, the missing command was added and the entire failover process was repeated. This time, the router successfully reclaimed the Active role, confirming that the issue had been resolved.

This repository contains the complete implementation, technical documentation, validation evidence, configuration files, and the GNS3 project required to reproduce the entire troubleshooting process.


## Objectives

The purpose of this lab was to gain a deeper understanding of how HSRP Version 2 operates in a real failover scenario.

During the development of the project, the following objectives were achieved:

- Configure HSRP Version 2 between two Cisco routers.
- Implement OSPF to provide end-to-end network connectivity.
- Validate communication through a shared virtual gateway.
- Simulate the failure of the Active router.
- Analyze the protocol behavior after the router recovered.
- Identify the reason why the Active role was not automatically restored.
- Apply the `preempt` feature to recover the expected HSRP behavior.
- Document every stage of the implementation, troubleshooting process, and final validation.


  ## Technologies Used

The lab was built using Cisco networking technologies and GNS3 to simulate a realistic enterprise environment.

- **GNS3** – Network simulation platform used to build and validate the laboratory.
- **Cisco IOS** – Operating system running on the simulated routers.
- **HSRP Version 2** – Configured to provide gateway redundancy and high availability.
- **OSPF** – Used as the dynamic routing protocol between the routers.
- **IPv4** – Addressing scheme implemented throughout the topology.
- **VPCS** – Lightweight virtual host used to validate end-to-end connectivity.


## Network Topology

The lab was designed using three Cisco routers and one VPCS client connected through a LAN segment.

OSPF was configured to provide routing between the routers, while HSRP Version 2 was implemented on the LAN to provide gateway redundancy through a shared virtual IP address.

This topology made it possible to simulate the failure of the Active router, observe how the Standby router took over the gateway role, and later validate the recovery process after enabling the missing HSRP feature.


## Repository Structure

The repository is organized according to each stage of the project, making it easier to follow the implementation, troubleshooting process, and final solution.

| Directory | Purpose |
|------------|---------|
| **Topologia** | Describes the network topology and IP addressing used in the lab. |
| **Configuraciones** | Contains the router configurations developed during each implementation phase. |
| **Evidencias** | Includes screenshots used to validate the implementation, troubleshooting process, and final solution. |
| **Documentacion** | Contains the technical analysis, root cause investigation, and conclusions. |
| **GNS3** | Stores the complete GNS3 project required to reproduce the laboratory. |


## Troubleshooting Scenario

The most important part of this lab was not the HSRP configuration itself, but understanding what happened after a failover.

Once the initial configuration was completed, Router 2 was operating as the Active router and Router 3 remained in the Standby state. To simulate a real network issue, the LAN interface of Router 2 was manually shut down.

As expected, Router 3 detected the loss of HSRP hello packets and assumed the Active role, allowing network connectivity to continue through the virtual gateway. Connectivity tests confirmed that the failover was successful and only a few packets were lost during the transition.

When Router 2 was brought back online, it rejoined the HSRP group but remained in the Standby state, even though it had a higher priority than Router 3. This unexpected behavior became the starting point of the troubleshooting process.

---

## Root Cause Analysis

After reviewing the HSRP configuration and validating the protocol states, it was determined that the issue was not related to routing or connectivity.

The behavior was caused by the absence of the `preempt` command. By default, HSRP does not force a router with a higher priority to take back the Active role after recovering from a failure. Instead, the current Active router continues forwarding traffic to avoid unnecessary role changes.

Because of this default behavior, Router 3 remained Active while Router 2 stayed in Standby after recovering.

---

## Solution

To restore the expected HSRP behavior, the `preempt` feature was enabled on Router 2, which was configured with the highest priority.

After applying the change, the failover test was repeated. This time, when Router 2 recovered, it automatically reclaimed the Active role while Router 3 returned to the Standby state.

The new behavior matched the expected operation of an HSRP deployment where the preferred router should resume its role after returning to service.

---

## Validation

The solution was verified by repeating the same tests performed before applying the fix.

The following validations confirmed that the issue had been resolved:

- HSRP state verification using `show standby brief`.
- Connectivity tests to the virtual IP address.
- End-to-end connectivity tests to the remote loopback network.
- Failover simulation by disabling the Active router.
- Recovery validation after enabling the `preempt` feature.

All screenshots and command outputs collected during these tests are available in the **Evidencias** directory.


## Conclusion

The purpose of this project was to understand how HSRP Version 2 behaves during a failover scenario and to document the complete troubleshooting process.

Beyond configuring the protocol, the main focus of this lab was to analyze an unexpected behavior, identify its root cause, validate the implemented solution, and document each stage of the process.

The result is a fully reproducible case study that includes the network topology, router configurations, technical documentation, validation evidence, and the complete GNS3 project. This repository serves as a practical reference for anyone who wants to learn how HSRP works or better understand a real troubleshooting process involving this technology.
