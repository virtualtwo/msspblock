## SECURE ENDPOINT MSSP SOC BLOCK

## Problem Statement

Currently to update a Simple Custome Detection (SCD) sha-256 file blocklist the MSSP partner must “log-in” to each tenants Secure Endpoint (AMP) instance and perform configuration manually for each customer. Example, imagine doing this procedure for 200+ Secure Endpoint tenants. This could also be done via API, via multiple posts.  This does not scale well and impacts efficiency of MSSP operations staff and thereby service revenue margins for the partner.  Secondarily, it would create additional work to create multiple integrations with different MSSP 3rd party platforms.

## Key Customer/Partner outcomes:
Automation to improve operational efficiency from hours to seconds.  This particular workflow can be leveraged for similar tasks like Application Block Lists as well.  A simple starting framework for other use cases that require common action across multiple MSSP Secure Endpoint customers.  Also provides a framework for SecureX threat response capabilities for investigating & remediating threats across multiple customers “simultaneously”.

## Invoking workflow from SecureX Threat Response context menu to block file across all MSSP customers.
![SX_CTR_Response](/SX_TR_ResponseAction.png)

## Invoking workflow from SecureX browser plug-in to block file across all MSSP customers.
![SX_BrowserResponse](/SX_Browser_Response.png)

## Invoking workflow from Secure Endpoint customer console context menu to block file across all MSSP customers.
![AMP Console Context Response](/Endpoint_ResponseAction.png)

## Learning Lab
https://developer.cisco.com/learning/modules/SecureX-orchestration
