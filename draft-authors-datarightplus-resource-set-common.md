%%%
title = "DataRight+: Common Resource Set"
area = "Internet"
workgroup = "datarightplus"
submissionType = "independent"

[seriesInfo]
name = "Internet-Draft"
value = "draft-authors-datarightplus-resource-set-common-latest"
stream = "independent"
status = "informational"

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

# Authorisation Scopes

Technical authorisation scopes are defined between Provider and Initiator and permit access to resource server endpoints. In addition, this specification also outlines the title and a simple description of the language to use to describe the data set referred to as Data Set Language.

Providers and Initiators **MUST** utilise the prescribed authorisation scopes and Data Set Language when seeking Consumer authorisation.

| `scope` value                 | Consumer Type | Data Set Language                                                                                                                                                                                                    |
|-------------------------------|---------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `common:customer.basic:read`  | Individual    | **Name and occupation**<br>Name;<br>Occupation;                                                                                                                                                                      |
| `common:customer.basic:read`  | Entity        | **Organisation profile**<br>Agent name and role;<br>Organisation name;<br>Organisation numbers (ABN or ACN);<br>Charity status;<br>Establishment date;<br>Industry;<br>Organisation type<br>Country of registration; |
| `common:customer.detail:read` | Individual    | **Contact Details**<br>Phone;<br>Email address;<br>Mail address;<br>Residential address;                                                                                                                             |
| `common:customer.detail:read` | Entity        | **Organisation contact details**<br>Organisation address;<br>Mail address;<br>Phone number;                                                                                                                          |

## Overlapping Scope Optimisation

In certain situations multiple technical scopes overlap which can lead to confusion by the User granting permission for the Consumer (which may be themselves or an entity they represent). In order to alleviate this Data Cluster Language presentation **MUST** be collapsed as follows:

| `scope` value(s)                                                  | Consumer Type | Data Set Language                                                                                                                                                                                                                                                                                    |
|----------------------------------------------------------------|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `common:customer.basic:read` and `common:customer.detail:read` | Individual    | **Name, occupation, contact details**<br>Name;<br>Occupation;<br>Phone;<br>Email address;<br>Mail address;<br>Residential address;                                                                                                                                                                   |
| `common:customer.basic:read` and `common:customer.detail:read` | Entity        | **Organisation profile and contact details**<br>Agent name and role;<br>Organisation name;<br>Organisation numbers (ABN or ACN);<br>Charity status;<br>Establishment date;<br>Industry;<br>Organisation type;<br>Country of registration;<br>Organisation address;<br>Mail address;<br>Phone number; |

# Providers

Providers are **REQUIRED** to deliver a number of authorisation and resource server capabilities.

## Authorisation Server

In addition to other provisions incorporated within the relevent ecosystem set, the Provider authorisation server **MUST**:

1. Support the `scope` parameters outlined within [Authorisation Scopes];

## Resource Server

The Provider **MUST** deliver the following endpoints, secured by the [Authorisation Server] with the specified `scope` parameters and in accordance with [@!DATARIGHTPLUS-REDOCLY]:

| HTTP Endpoint                 | Authorisation Scope            | OpenAPI Operation ID | Supported `x-v` Parameters |
|-------------------------------|--------------------------------|----------------------|----------------------------|
| `GET /common/customer`        | `common:customer.basic:read`   | `getCustomer`        | `1`                        |
| `GET /common/customer/detail` | `common:customer.basic:detail` | `getCustomerDetail`  | `1`                        |

In addition the Provider **MUST** deliver the following endpoints, without authentication and generally available, in accordance with [@!DATARIGHTPLUS-REDOCLY]:

| HTTP Endpoint            | OpenAPI Operation ID | Supported `x-v` Parameters |
|--------------------------|----------------------|----------------------------|
| `GET /discovery/outages` | `getOutages`         | `1`                        |
| `GET /discovery/status`  | `getStatus`          | `1`                        |

# Initiators

This specification contains no additional provisions for Initiators.

# Acknowledgement

The following people contributed to this document:

- Stuart Low (Biza.io) - Editor

We acknowledge the contribution to the [@!CDS] of the following individuals:
- James Bligh (Data Standards Body) - Lead Architect for the Consumer Data Right
- Mark Verstege (Data Standards Body) - Lead Architect, Banking & Information Security for the Consumer Data Right
- Ivan Hosgood (formerly Data Standards Body & ACCC) - Solutions Architect

{backmatter}

<reference anchor="DATARIGHTPLUS-REDOCLY" target="https://datarightplus.github.io/datarightplus-redocly/"> <front><title>DataRight+: Redocly</title><author initials="S." surname="Low" fullname="Stuart Low"><organization>Biza.io</organization></author><author initials="B." surname="Kolera" fullname="Ben Kolera"><organization>Biza.io</organization></author>
<author initials="W." surname="Cai" fullname="Wei Cai"><organization>Biza.io</organization></author></front> </reference>

<reference anchor="DATARIGHTPLUS-ROSETTA" target="https://datarightplus.github.io/datarightplus-specs/main/datarightplus-rosetta.html"> <front><title>DataRight+ Rosetta Stone</title><author initials="S." surname="Low" fullname="Stuart Low"><organization>Biza.io</organization></author></front> </reference>

<reference anchor="CDS" target="https://consumerdatastandardsaustralia.github.io/standards"><front><title>Consumer Data Standards (CDS)</title><author><organization>Data Standards Body (Treasury)</organization></author></front> </reference>

<reference anchor="DATARIGHTPLUS-INFOSEC-SHARING-V1" target="https://datarightplus.github.io/datarightplus-specs/main/datarightplus-infosec-sharing-v1.html"> <front><title>CDR: Sharing Arrangement V1</title><author initials="S." surname="Low" fullname="Stuart Low"><organization>Biza.io</organization></author></front> </reference>

<reference anchor="OIDC-Core" target="http://openid.net/specs/openid-connect-core-1_0.html"> <front> <title>OpenID Connect Core 1.0 incorporating errata set 1</title> <author initials="N." surname="Sakimura" fullname="Nat Sakimura"></author></front></reference>

<reference anchor="TDIF" target="https://www.digitalidentity.gov.au"><front><title>Trusted Digital Identity Framework (
TDIF)</title><author><organization>Commonwealth of
Australia (Digital Transformation Agency)</organization></author></front> </reference>






