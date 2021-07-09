## Problem Statement.

Currently to update a Simple Custome Detection (SCD) sha-256 block list the MSSP partner must “log-in” to each tenants Secure Endpoint (AMP) instance and perform configuration manually for each customer. Example, imagine doing this procedure for 200+ Secure Endpoint tenants. This could also be done via API, via multiple posts.  This does not scale well and impacts efficiency of MSSP operations staff and thereby service revenue margins for the partner.  Secondarily, it would create additional work to create multiple integrations with different MSSP 3rd party platforms.

## Key Customer/Partner outcomes:
Automation to improve operational efficiency from hours to seconds.  This particular workflow can be leveraged for similar tasks like Application Block Lists as well.  A simple starting framework for other use cases that require common action across multiple MSSP Secure Endpoint customers.  Also provides a framework for SecureX threat response capabilities for investigating & remediating threats across multiple customers “simultaneously” via response context menu's.

## Pre-Requisites
* Acquire each tenant/customer API keys from Secure Endpoint MSSP Console
* Utilize Copy-AMP-MSSP-CREDS.json workflow to add Secure Endpoint customer tenant API keys into Group Target
* Configure each tenant customer with Outbreak Control Blocklist-Simple Custom Detection using common name across all tenant customers (e.g. MSSP_SOC_BLOCK)
![OutbreakControl](/OutbreakCtl_config.png)
* Add the common name Outbreak Control-Simple Custom Detection list in relevant Computer group policies in each tenant customer.
![CustomerPolicy](/EndpointPolicy_SCD.png)

## Worflow Operation
Loop through each MSSP customer and do the following:
1. Get all Simple Custom Detection Lists (SCD)
1. Create a table with each SCD list name & GUID
1. Select SCD list table entry with name "MSSP_SOC_BLOCK" and extract list GUID
1. Update customer SCD list GUID named MSSP_SOC_BLOCK with input SHA-256 value 
1. Verify input SHA-256 is contanined in SCD list named "MSSP_SOC_BLOCK"
1. Creates table for Successful and Failed updates for each customer.

![MSSP_SOC_BLOCK_Workflow](https://wwwin-github.cisco.com/dallong/SXO_hackathon_MSSP_SOC/blob/master/Screen%20Shot%202021-04-19%20at%202.07.33%20PM.png)



## Required Global Variable
Create Global Variable MSSP customer credentials using Copy-ADD-AMP-MSSP-CREDS.json to aggregate MSSP customer API account keys used in this workflow.

## Required Targets
* AMP Target
* AMP MSSP Target Group - contains all MSSP customer targets

## Required Account Keys
* Account keys for each individual AMP-MSSP Customer 
* Global MSSP Account Keys

## Setup Information
Browse to your SecureX orchestration instance. This wille be a different URL depending on the region your account is in:

* US: https://securex-ao.us.security.cisco.com/orch-ui/workflows/
* EU: https://securex-ao.eu.security.cisco.com/orch-ui/workflows/
* APJC: https://securex-ao.apjc.security.cisco.com/orch-ui/workflows/

Import both workflows.
* Copy-ADD-AMP-MSSP-CREDS.json
* AMP MSSP Customer Block List.json

## Running Workflow

* SecureX Orchestration directly
![SXO_RUN](/SXO_Run.png)

* Threat Response context menu in SecureX Threat Response
![SX_CTR](/SX_TR_ResponseAction.png)

* SecureX browser plug-in.
![SX_BROWSER](/SX_Browser_Response.png)

* Secure Endpoint Customer/Tenant console
![ENDPOINT_CONSOLE](/Endpoint_ResponseAction.png)


## Notes
* In this workflow the named SCD List "MSSP_SOC_BLOCK" could be any name for the SCD, but it must be consistent across all customers to succeed.

