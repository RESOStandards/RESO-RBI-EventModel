
# RESO Distributed Ledger Event Model

## Request Change Proposal 

**Submitter Name**: Ashish Antal    
**Submitter Organization**:  MLSListings 
**Submitter Email**:  aantal@mlslistings.com 

**Date Submitted**:  6/12/2019 
**Proposal Number**: 004  
**Status**: Submitted  
**Status Change Date**: 01/12/2019  

## Synopsis
Define a scheme for recording **Subject** and **Recorder** identifiers  
## Rationale
Identifiers created and supplied by recording system should follow a standard scheme to allow parsing and referencing external/native data records
## Proposal 
Adopt **Universal Resource Naming** scheme:

<img src="https://upload.wikimedia.org/wikipedia/commons/c/ce/URN_syntax_diagram_-_namestring.png" /> 

### Event Subject Identifiers
examples:

URN|Corresponds To
:--- | :---
urn:reso:listingkeynumeric:81123456| A listing identifier in an Org 
urn:reso:agentkeynumeric:1221211| An agent identifier in an Org 
urn:reso:percelnumber:122-212-12331| A property tax record identifier in an Org  
urn:reso:upid:122-12-1331-N-R| A reso UPID (Unique Property Identifier)
urn:uuid:6e8bc430-9c3a-11d9-9669-0800200c9a66| A GUID (Global Unique Identifier)

### Event Recorder Identifiers
examples:

URN|Corresponds To
:--- | :---
urn:reso:recorder:org1:1234| Event catalog recording entity identifier for a recorder in Org 1
urn:reso:recorder:org2:1143| Event catalog recording entity identifier for a recorder in Org 2
