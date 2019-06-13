
# RESO Distributed Ledger Event Model

## Request Change Proposal 

**Submitter Name**:    
**Submitter Organization**: eXp  
**Submitter Email**:   

**Date Submitted**:   6/13/2019
**Proposal Number**: 002  
**Status**: Submitted  
**Status Change Date**: 6/13/2019 

## Synopsis
Agent and Broker office activitity events are not defined 
## Rationale
Events related to agents and broker office will allow systems to send notification, interact with each other and track internal tasks
## Proposal 
Add the following events to track agent and broker business tasks, functions and process status:

### Proposed Events
Event|Description
:--|:--
Application|A new application tringgering a process
Personal|Personal information records
License1|Primary license information
License2|Additional lincense information
Experience|Experince records
Financial|Financial records
Verification|Verification stage in a process
Approval|Approval stage in a process
Review|Reviwing stage in a process
Transfer|Record transfer process 
Email|Email verification process 
ICA|Indipendent Contract Aggreement 
Firm|Organizaiton related activity
Agent|Agent related activing

### Proposed Actions
Action|Description
:--|:--
Started|A process has started
Provided|Information related to an event was provided
Signed|A document was signed
Verified|Information related to an event was verified
Denied|Information access, service request or process approval was denied
Complete|A process or stage in a process was completed
Failed|A process or task has failed
Transferred|Documents or records were transferred
Joined|A subject joined an organization, task or process 
Active|Task or process status indicator


### Exapmple of Events and Actions Combined
Event|Action|Description
:--|:--|:--
Application|Started|A new application 
Personal|Provided|Prosonal information records
License1|Provided|Primary license data
License2|Provided|Additional license data
Experience|Provided|Personal experience records
Financial|Provided|Financial records
ICA|Signed|Contract agreement
License1|Verified|Primary license verification
License2|Verified|Additional license verification
License1|Approved|Primary license approval
License2|Approved|Additional license approval
License1|Denied|Primary license denial
License2|Denied|Additional license denial
Verification|Complete|Successful verificaion 
Verification|Failed|Failure in a verificaion process
Approval|Complete|Applicaion approval
Review|Complete|Completion of review process
License1|Transferred|Transfer of agents primary license
License2|Transferred|Transfer of agents additionl license
Transfer|Completed|Completion of transfer process
Email|Verified|Email verificaion 
Organizaion|Joined|Subject joining an organizaiton
Agent|Active|Status indicator

