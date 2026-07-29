# Documentation

This directory contains the technical documentation related to the HSRP v2 troubleshooting case study.

## Contents

- **Root_Cause_Analysis.md**  
  Technical analysis describing the failover behavior, the identified root cause, and the reasoning behind the solution.


  ---

# Solution Validation (Preempt Enabled)

The following screenshots validate the implementation of the HSRP `preempt` feature and demonstrate that the router with the highest priority automatically regains the Active role after recovering from a failure.

| File | Description |
|------|-------------|
| 12_Preempt_Configuration.png | HSRP configuration showing the `standby 10 preempt` command enabled on R2. |
| 13_R3_Active_During_Failover.png | R3 becomes the Active router after the failure of R2. |
| 14_R2_Reclaims_Active.png | R2 automatically regains the Active role after recovering. |
| 15_R3_Returns_To_Standby.png | R3 returns to the Standby state after R2 resumes the Active role. |
