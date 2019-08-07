
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


### notes:
  ## Colon character
   Because the colon character (":") is used to separate "urn" from the
   NID and the NID from the NSS, it's tempting to think of the entire
   URN as being structured by colon characters and to assume that colons
   create a structure or hierarchy within the NSS portion of the URN.
   Such structure could be specified by a particular NID specification,
   but there is no implicit structure.  In a URN such as

      urn:example:apple:pear:plum:cherry

   the NSS string is "apple:pear:plum:cherry" as a whole, and there is
   no specific meaning to the colon characters within that NSS string
   unless such meaning is described in the specification of the
   "example" namespace.
   
  
  ## URN-equivalence rules

   This section shows a variety of URNs (using the "example" NID defined
   in [RFC6963]) that highlight the URN-equivalence rules.

   First, because the scheme and NID are case insensitive, the following
   three URNs are URN-equivalent to each other:

   o  urn:example:a123,z456

   o  URN:example:a123,z456

   o  urn:EXAMPLE:a123,z456

   Second, because the r-component, q-component, and f-component are not
   taken into account for purposes of testing URN-equivalence, the
   following three URNs are URN-equivalent to the first three examples
   above:

   o  urn:example:a123,z456?+abc

   o  urn:example:a123,z456?=xyz

   o  urn:example:a123,z456#789

   Third, because the "/" character (and anything that follows it) in
   the NSS is taken into account for purposes of URN-equivalence, the
   following URNs are not URN-equivalent to each other or to the six
   preceding URNs:

   o  urn:example:a123,z456/foo

   o  urn:example:a123,z456/bar

   o  urn:example:a123,z456/baz

   Fourth, because of percent-encoding, the following URNs are
   URN-equivalent only to each other and not to any of those above (note
   that, although %2C is the percent-encoded transformation of "," from
   the previous examples, such sequences are not decoded for purposes of
   testing URN-equivalence):

   o  urn:example:a123%2Cz456

   o  URN:EXAMPLE:a123%2cz456


   Fifth, because characters in the NSS other than percent-encoded
   sequences are treated in a case-sensitive manner (unless otherwise
   specified for the URN namespace in question), the following URNs are
   not URN-equivalent to the first three URNs:

   o  urn:example:A123,z456

   o  urn:example:a123,Z456

   Sixth, on casual visual inspection of a URN presented in a human-
   oriented interface, the following URN might appear the same as the
   first three URNs (because U+0430 CYRILLIC SMALL LETTER A can be
   confused with U+0061 LATIN SMALL LETTER A), but it is not
   URN-equivalent to the first three URNs:

   o  urn:example:%D0%B0123,z456
   
   
   ### references:
   https://tools.ietf.org/html/rfc8141
   
