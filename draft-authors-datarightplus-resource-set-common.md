%%%
title = "DataRight+: Common Resource Set"
area = "Internet"
workgroup = "datarightplus"
submissionType = "independent"

[seriesInfo]
name = "Internet-Draft"
value = "draft-authors-datarightplus-resource-set-common-latest"
stream = "independent"
status = "experimental"

date = 2024-03-28T00:00:00Z

[[author]]
initials="S."
surname="Low"
fullname="Stuart Low"
organization="Biza.io"
[author.address]
email = "stuart@biza.io"

%%%

.# Abstract

This is the resource set profile outlining the common endpoints utilised across multiple industries.

.# Notational Conventions

The keywords "**REQUIRED**", "**SHALL**", "**SHALL NOT**", "**SHOULD**", "**SHOULD NOT**", "**RECOMMENDED**",  "**MAY**", and "**OPTIONAL**" in this document are to be interpreted as described in [@!RFC2119].

{mainmatter}

# Scope

The scope of this document is intended to be limited to the shared resource server endpoints, and their associated authorisation contexts.

# Terminology

This specification utilises the various terms outlined within [@!DATARIGHTPLUS-ROSETTA].

# Providers

Providers are expected to deliver a set of common resource server endpoints.

## Authorisation Server

In addition to other provisions incorporated within the relevant ecosystem set, the Provider authorisation server **SHALL**:

1. Support the [@!RFC6749] `scope` parameter with possible values outlined within [Authorisation Scopes](#name-authorisation-scopes);

### Authorisation Scopes

The Provider authorisation server **SHALL** utilise the following Data Set Language when seeking authorisation from a Consumer representing an Individual for specific `scope` values:

| `scope` value                 | Data Set Language                  |
|-------------------------------|------------------------------------|
| `common:customer.basic:read`  | **Name and occupation**            |
|                               | Name;                              |
|                               | Occupation;                        |
|                               |                                    |
| `common:customer.detail:read` | **Contact Details**                |
|                               | Phone;                             |
|                               | Email address;                     |
|                               | Mail address;                      |
|                               | Residential address;               |
|                               |                                    |

The Provider authorisation server **SHALL** utilise the following Data Set Language when seeking authorisation from a Consumer representing an Entity for specific `scope` values:

| `scope` value                 | Data Set Language                  |
|-------------------------------|------------------------------------|
| `common:customer.basic:read`  | **Organisation profile**           |
|                               | Agent name and role;               |
|                               | Organisation name;                 |
|                               | Organisation numbers (ABN or ACN); |
|                               | Charity status;                    |
|                               | Establishment date;                |
|                               | Industry;                          |
|                               | Organisation type                  |
|                               | Country of registration;           |
|                               |                                    |
| `common:customer.detail:read` | **Organisation contact details**   |
|                               | Organisation address;              |
|                               | Mail address;                      |
|                               | Phone number;                      |
|                               |                                    |

### Overlapping Scope Optimisation

Alternative Data Cluster Language **SHALL** be used for Consumers representing Individuals when pairs of `scope` value are used as follows:

| `scope` pairing                  | Data Set Language                            |
|----------------------------------|----------------------------------------------|
| `common:customer.basic:read` and | **Name, occupation, contact details**        |
| `common:customer.detail:read`    | Name;                                        |
|                                  | Occupation;                                  |
|                                  | Phone;                                       |
|                                  | Email address;                               |
|                                  | Mail address;                                |
|                                  | Residential address;                         |
|                                  |                                              |


Alternative Data Cluster Language **SHALL** be used for Consumers representing Entities when pairs of `scope` value are used as follows:

| `scope` pairing                  | Data Set Language                            |
|----------------------------------|----------------------------------------------|
| `common:customer.basic:read` and | **Organisation profile and contact details** |
| `common:customer.detail:read`    | Agent name and role;                         |
|                                  | Organisation name;                           |
|                                  | Organisation numbers (ABN or ACN);           |
|                                  | Charity status;                              |
|                                  | Establishment date;                          |
|                                  | Industry;                                    |
|                                  | Organisation type;                           |
|                                  | Country of registration;                     |
|                                  | Organisation address;                        |
|                                  | Mail address;                                |
|                                  | Phone number;                                |
|                                  |                                              |

## Resource Server

The Provider **SHALL** make available, as described further in [@!DATARIGHTPLUS-REDOCLY-ID1] endpoints, the following endpoints where the token is granted the `common:customer.basic:read` scope value:

| Resource Server Endpoint      | Authorisation Scope            | `x-v` |
|-------------------------------|--------------------------------|-------|
| `GET /common/customer`        | `common:customer.basic:read`   | `1`   |

The Provider **SHALL** make available, as described further in [@!DATARIGHTPLUS-REDOCLY-ID1] endpoints, the following endpoint where the token is granted the `common:customer.basic:detail` scope value:

| Resource Server Endpoint      | Authorisation Scope            | `x-v` |
|-------------------------------|--------------------------------|-------|
| `GET /common/customer/detail` | `common:customer.basic:detail` | `1`   |


The Provider **SHALL** also deliver the following unauthenticated and generally available endpoints, in accordance with [@!DATARIGHTPLUS-REDOCLY-ID1]:

| Resource Server Endpoint | `x-v` |
|--------------------------|-------|
| `GET /discovery/outages` | `1`   |
| `GET /discovery/status`  | `1`   |

# Initiators

Initiators **SHALL** describe the requested `scope` values using the same Data Set Language as Providers, as outlined in [Authorisation Scopes](#name-authorisation-scopes).

# Acknowledgement

The following people contributed to this document:

- Stuart Low (Biza.io) - Editor

We acknowledge the contribution to the [@!CDS] of the following individuals:

- James Bligh (Data Standards Body) - Lead Architect for the Consumer Data Right
- Mark Verstege (Data Standards Body) - Lead Architect, Banking & Information Security for the Consumer Data Right
- Ivan Hosgood (formerly Data Standards Body & ACCC) - Solutions Architect

{backmatter}

<reference anchor="DATARIGHTPLUS-REDOCLY-ID1" target="https://datarightplus.github.io/datarightplus-redocly/?v=ID1"> <front><title>DataRight+: Redocly (ID1)</title><author initials="S." surname="Low" fullname="Stuart Low"><organization>Biza.io</organization></author><author initials="B." surname="Kolera" fullname="Ben Kolera"><organization>Biza.io</organization></author>
<author initials="W." surname="Cai" fullname="Wei Cai"><organization>Biza.io</organization></author></front> </reference>

<reference anchor="DATARIGHTPLUS-ROSETTA" target="https://datarightplus.github.io/datarightplus-rosetta/draft-authors-datarightplus-rosetta.html"> <front><title>DataRight+ Rosetta Stone</title><author initials="S." surname="Low" fullname="Stuart Low"><organization>Biza.io</organization></author></front> </reference>

<reference anchor="CDS" target="https://consumerdatastandardsaustralia.github.io/standards"><front><title>Consumer Data Standards (CDS)</title><author><organization>Data Standards Body (Treasury)</organization></author></front> </reference>







