
# RESO Distributed Ledger Event Model

## Request for Comment 

#### Submitted to RESO Distributed Ledger Worgroup by the Real Estate Blockchain Initiative
#### Version 1.3 - April 2019

---

## Table of Contents  

- [Overview](#overview)
- [Usage](#usage)
- [Examples](#examples)
 - [History of a home being sold](#history-of-a-home-being-sold)
 - [Construction project](#construction-project)
- [Lookup Fields](#lookups)
  - [Entity](#entity-lookup)
  - [Event](#event-lookup)
  - [State](#state-lookup)
  - [SubjectType](#subjecttype-lookup)
  - [System](#system-lookup)
  - [ReferenceType](#referencetype-lookup)
- [Assigned Fields](#assigned-fields)
  - [Application](#application)
  - [EventSubject](#eventsubject)
  - [Reference](#reference)
  - [Timestamp](#timestamp)
  - [TransactionId](#transactionid)
  - [Version](#version)

---

## Overview  

An event is a record of occurrence that relects the state of a document,
process, system,  or object as of a point in time.  Events expressed with a
standard approach are easier to store and pass between systems.  The RESO
Distributed Ledger Event Model represents a standard approach that can be used
to reliably record, playback, and communicate events.     

The Event Model is an application communication standard that is independent of
the underlying systems on each side.  It is ideal for integrating traditional
systems with distributed ledgers in a business-to-business (B2B) arrangement.  
The model can also be used to connect websites with distributed ledgers in a 
business-to-consumer (B2C) scenario.   

All of the components of the model are expressed as JSON formatted objects
conforming to RFC 8259 and ECMA-404.  

There are ten fields that are used to represent an Event:

Field | Responsibility | Scope | Description
:--- | :--- | :--- | :---
[TransactionId](#transactionid) | System Assigned | Unique within the ledger | A unique identifier created for each recording in an immutable ledger
[EventSubject](#eventsubject) | Application Supplied | Opaque to the ledger | Uniquely identifies the object of the event. e.g. Unique Property Identifier, Unique Agent Identifier, Unique Organization Identifier, etc.
[System](#system-lookup) | Lookup | [System Value](#system-values) | Classification of the business system generating the event. The type of user is handled by the [Entity](#entity-lookup) lookup.
[SubjectType](#subjecttype-lookup) | Lookup | [SubjectType Value](#subjecttype-values) | Classification of the object the event is being applied to; the noun.  Related to the EventSubject.
[Entity](#entity-lookup) | Lookup | [Entity Value](#entity-values) | Classification of the what generated the event; the actor.   A person uses a [System](#system-lookup) to record events.
[Event](#event-lookup) | Lookup | [Event Value](#event-values) | Describes a document, occurrence , or incident.  Typically has associated documentation. Further classified by [State](#state-lookup).
[State](#state-lookup) | Lookup | [State Value](#state-values) | A verb identifying the occurrence being recorded.  Expressed in terms of the [Event](#event-lookup) argument.
[ReferenceType](#referencetype-lookup) | Lookup | [ReferenceType Value](#referencetype-values) | Classification of the insformation contained in the  [Reference](#reference) field.
[Reference](#reference) | Application Supplied | Opaque to the ledger | A value that can be used as a cross reference to tother systems.  The [ReferenceType](#referencetype-lookup) value provides further context.
[Timestamp](#timestamp) | System Assigned | UTC timestamp | The underlying distributed ledger assigns this field.
[Version](#version) | System Assigned | Version of this standard | The underlying distributed ledger assigns this field
[Application](#application) | Application Supplied | Opaque to the ledger | Identifies the application or system used to record the event; the system of record.

There is a section of this document that describes each of the Lookup types (System, Resource, etc.).

### Notes

1. System Assigned arguments (TransactionId, Timestamp, and Version) are
created by the distributed ledger.  They should not proprietary to the
distributed ledger being used.

2. Application Supplied arguments (EventSubject and Application) have meaning
to the recording application.  The ledger does not operate on these fields and
should pass them unaltered.

3. The Version argument governs which verson of the standard is be used for
representation.  The set of lookups can change between versions of the standard.

4. Applications are responsible for reconciling records with different versions.

---

## Usage  

The RESO Event Model is a communications format and is not dependent on systems
that create or consume events.

Events are created by Event Producers and be either traditional systems or 
distributed ledgers.  After the event is created, it is formatted into the RESO
Event Model format and transmitted to other applications.

```
                                                     .---------------.
                                                     |  Distributed  |
  .---------------.                            .---->|    Ledger     |
  |  Distributed  |                            |     '---------------'
  |    Ledger     |---.                        |     .---------------.
  '---------------'   |                        |     |      Web      |
                      |------------------------|---->|  Application  |
  .---------------.   |       RESO Event       |     '---------------'
  |  Traditional  |---'          Model         |     .---------------.
  |    System     |                            |     |  Traditional  |
  '---------------'                            '---->|    System     |
                                                     '---------------'

        Event                                              Event
      Producers                                          Consumers
```
Applications that consumer RESO Event Model formatted events are called Event
Consumers.  An Event Consumer can be a web application, traditional system, or
a distributed ledger.  
 

---

## Examples

This section presents normative examples of the event model.  These are simple
examples intended to demonstrate the model.  All of the records use the
[EventSubject](#eventsubject) field to represent the same property; RESO UPI
(US-42049-49888-1213666-R-N).


### History of a home being sold

Each record represents an event.  The records have been sorted by the
[Timestamp](#timestamp) field to present the chronological sequencing of the
history.  

[TransactionId](#transactionid) | [EventSubject](#eventsubject) | [System](#system-lookup) | [SubjectType](#subjectType-lookup) | [Entity](#entity-lookup) | [Event](#event-lookup) | [State](#state-lookup) | [ReferenceType](#referencetype-lookup) | [Reference](#reference) | [Timestamp](#timestamp) | [Application](#application) 
:--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :---
4b46aadd-0f2a-4e79-b3a6-e2e45927d2a2 | US-42049-49888-1213666-R-N | Property Listing Service | Property | Broker | Listing | Recorded | None | [NO VALUE] | Sun, 03 Jun 2018 13:04:05 GMT | 87478-a43
c7e5a353f-d3b4-2f48-8f02-604bbe507805 | US-42049-49888-1213666-R-N | Property Listing Service | Property | Broker | Listing | Changed | None | [NO VALUE] | Sat, 21 Jul 2018 18:34:22 GMT | 87478-a43
cd7a53f-d3b4-4e48-845b-604bbe507805 | US-42049-49888-1213666-R-N | Property Marketing Service | Property | Agent | Openhouse | Published | URI | https://sample_open_house.com?US-42049-49888-1213666-R-N | Sun, 19 Aug 2018 12:01:45 GMT | 15435-dd6
2ad753f4-d3b4-4e47-8402-604bbe7886434 | US-42049-49888-1213666-R-N | Property Listing Service | Property | Broker | Offer | Received | None | [NO VALUE] | Tue, 28 Aug 2018 18:11:22 GMT | 87478-a43
e27a353f-d3b4-32e8-8629-604bbe237802 | US-42049-49888-1213666-R-N | Transaction Management Service | Property | Broker | Contract | Signed | None | [NO VALUE] | Wed, 03 Oct 2018 12:011:48 GMT | 438-f32

### Construction project

Each record represents an event.  The records have been sorted by the
[Timestamp](#timestamp) field to present the chronological sequencing of the
history.  

[TransactionId](#transactionid) | [EventSubject](#eventsubject) | [System](#system-lookup) | [SubjectType](#subjectType-lookup) | [Entity](#entity-lookup) | [Event](#event-lookup) | [State](#state-lookup) | [ReferenceType](#referencetype-lookup) | [Reference](#reference) | [Timestamp](#timestamp) | [Application](#application) 
:--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :---
4b46aadd-0f2a-4e79-b3a6-e2e45927d2a2 | US-42049-49888-1213666-R-N | Tax Assessment System | Tax | County | Assessment | Received | None | [NO VALUE] | Thu, 14 Jun 2017 13:04:05 GMT | 87478-a43
c7e5a353f-d3b4-2f48-8f02-604bbe507805 | US-42049-49888-1213666-R-N | Mortgage Industry Service | Loan | Builder | Estimate | Received | None | [NO VALUE] | Sat, 21 Jul 2018 18:34:22 GMT | 87478-a43
cd7a53f-d3b4-4e48-845b-604bbe507805 | US-42049-49888-1213666-R-N | Property Recording System | Loan | Builder | Lien  | Placed | URI | https://conty_recorder.com?US-42049-49888-1213666-R-N | Sun, 19 Aug 2018 12:01:45 GMT | 15435-dd6
2ad753f4-d3b4-4e47-8402-604bbe7886434 | US-42049-49888-1213666-R-N | Manual Input | Loan | Builder | Construction | Completed | None | [NO VALUE] | Tue, 28 Aug 2018 18:11:22 GMT | 87478-a43
e27a353f-d3b4-32e8-8629-604bbe237802 | US-42049-49888-1213666-R-N | Property Recording System | Loan | Builder | Lien | Removed | None | [NO VALUE] | Wed, 03 Oct 2018 12:011:48 GMT | 438-f32
7646aaef-ec2a-4e79-b5a6-e2e39827d0a5 | US-42049-49888-1213666-R-N | Tax Assessment System | Tax | County | Assessment | Received | None | [NO VALUE] | Thu, 13 Dec 2018 14:08:23 GMT | 87478-a43

---

## Lookup Fields 

Lookups are used to avoid freeform text in event fields.  Users are typically
presented the options for these fields as drop-downs. Lookup values are not
codified, therefore the entire text value is used in the record.

Values in addition those presented are not valid.  In order to add values to
lookup fields, the specification should bbe revised with a new version.

### Entity Lookup

The Entity Lookup is the clasification of what kind of person is acting as a 
recorder.  The person records events using a [System](#system-lookup).

#### Entity Values

+ Agent
+ Broker
+ Builder
+ Buyer
+ City
+ County
+ Escrow
+ Lender
+ MLS
+ Owner
+ Vendor

### Event Lookup

The Event Lookup classifies a document or documented occurrence that is 
associated with the record.  Further classified by [State](#state-lookup).  

#### Event Values

+ Application
+ Appraisal
+ Assessment
+ Construction
+ Contract
+ Deed
+ Estimate
+ Identity
+ Improvement
+ Lien
+ Listing
+ Offer
+ Openhouse
+ Permit
+ Price
+ Referral
+ Status

### State Lookup

The State Lookup classifies what specifically is being recorded about the 
[Event](#event-lookup).  It represents an action or verb.

#### State Values

+ Accepted
+ Changed
+ Closed
+ Completed
+ Created
+ Funded
+ Placed
+ Received
+ Recorded
+ Rejected
+ Removed
+ Signed
+ Published

### SubjectType Lookup

The SubjectType Lookup classifies what is being modified by the record.  It 
identifies what is in the [Event Subject](#eventsubject) Field.

#### SubjectType Values

+ Agent
+ Loan
+ Office
+ Property
+ Referral
+ Tax
+ Transaction

### System Lookup

The System Lookup classifies the system generating the record.  It is related
to the [Application](#application) field which identifies the software creating
the record. It is also related to the [Entity](#entity-lookup) lookup which
identifies what kind of user is creating the record.  

#### System Values

+ Property Listing Service
+ Property Registration Service
+ Broker Referral Tracking
+ Mortgage Industry Service
+ Property Marketing Service
+ Property Recording System
+ Tax Assessment System
+ Transaction Management Service
+ Manual Input

### ReferenceType Lookup

The Reference Lookup classifies the reference for the event.  It is related
to the [Reference](#reference) field identifying the format to expect in the 
[Reference](#reference) field.   

The ReferenceType of URI identifies the value in the [Reference](#reference) 
field as conforming to RFC 3986.  A URI can be a URL or a namespace identifier. 

#### ReferenceType Values

+ None 
+ URI 

---

## Assigned Fields 

Assigned event fields contain freeform text.  These fields are assigned by
applications.

### Application 

EventSubject is comprised of alphanumeric digits and hyphens only. Letters are
not case-sensitive.  Identifies the application or system used to record the
event.  It represents the system of record.

### EventSubject 

EventSubject is comprised of alphanumeric digits and hyphens only. Letters are
not case-sensitive.  This format is compatible with the RESO Universal Property
Identifier format.  An EventSubject can also represent other RESO values such
as the Universal Agent Identifier and Universal Organization Identifier.

### Reference 

Reference is comprised of alphanumeric digits and hyphens only. Letters are
not case-sensitive.  This format of the field is goverened by the
[ReferenceType](#referencetype-lookup) value.  This field is commonly contains a
URL that provides more detail information about the event. If there is no 
reference for the event, the field can be omitted. 

### Timestamp 

The underlying distributed ledger assigns this field and it should represent
UTC time.

### TransactionId 

A unique identifier created by the ledger for each recording.  The value should
be independent of the distribbuted ledger.

### Version 

Version represent which verson of the standard is be used for the event.  The
set of lookups can change between versions of the standard and applications are
responsible for reconciling records with different versions.

Additional lookup values (to the values presented in this docuemnt)  are not
valid.  Add additional values to lookup fields requires a revision of the
specification.

---
