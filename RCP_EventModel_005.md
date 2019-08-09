# RESO Distributed Ledger Event Model

## Request Change Proposal 

**Submitter Name**: Claudio Ceballos Paz    
**Submitter Organization**:  Reconsortia  
**Submitter Email**:  claudio@reconsortia.com 

**Date Submitted**:  7/8/2019 
**Proposal Number**: 005  
**Status**: Submitted  
**Status Change Date**:   

## Synopsis
Add extra values to support referals events.
## Rationale
Referral lifecycle should follow a standard denomination and states.

## Proposal 
Add the following to the [Event Ledger V1.3](https://github.com/RESOStandards/RESO-RBI-EventModel#reso-distributed-ledger-event-model):

## Lookup Fields
### Entity Lookup
The Entity Lookup is the clasification of what kind of person is acting as a recorder. The person records events using a System.

#### Entity Values
New are proposed in **bold**.

* Agent
* Broker
* Builder
* Buyer
* City
* County
* Escrow
* Lender
* MLS
* Owner
* Vendor
* **Transaction coordinator** 


Proposal|Description
:--|:--
Transaction coordinator|Can upload documents to the ledger

### Event Lookup
The Event Lookup classifies a document or documented occurrence that is associated with the record. Further classified by State.

#### Event Values
New are proposed in **bold**.

* Application
* Appraisal
* Assessment
* Construction
* Contract
* Deed
* Estimate
* Identity
* Improvement
* Lien
* Listing
* Offer
* Openhouse
* Permit
* Price
* Referral
* Status
* **Subreferrals** 
* **Compensation**
* **Source**
* **Destination**

Proposal|Description
:--|:--
Subreferrals|The referral could be divided
Compensation|The conpensation needs to be recorded
Source|To specify who is the referring broker/agent 
Destination|To specify who is the recipient broker/agent

### State Lookup
The State Lookup classifies what specifically is being recorded about the Event. It represents an action or verb.

#### State Values

New are proposed in **bold**. 

* Accepted
* Changed
* Closed
* Completed
* Created
* Funded
* Placed
* Received
* Recorded
* Rejected
* Removed
* Signed
* Published
* **Added**
* **Splitted**

Proposal|Description
:--|:--
Added|Information could be added after the referral is created.
Splitted|The referral is split into sub referrals. 



### SubjectType Lookup
The SubjectType Lookup classifies what is being modified by the record. It identifies what is in the Event Subject Field.

#### SubjectType Values
New are proposed in **bold**. 

* Agent
* Loan
* Office
* Property
* Referral
* Tax
* Transaction
* **Subreferral**

Proposal|Description
:--|:--
Subreferral|Information could be added after the referral is created.

### System Lookup
The System Lookup classifies the system generating the record. It is related to the Application field which identifies the software creating the record. It is also related to the Entity lookup which identifies what kind of user is creating the record.

#### System Values
New are proposed in **bold**. 

* Property Listing Service
* Property Registration Service
* Broker Referral Tracking
* Mortgage Industry Service
* Property Marketing Service
* Property Recording System
* Tax Assessment System
* Transaction Management Service
* Manual Input
* **Referral Marketplace Service**

Proposal|Description
:--|:--
Referral Marketplace Service|Events are originated in a Referral Marketplace.

