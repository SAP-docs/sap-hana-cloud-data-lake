<!-- loioa3de3db284f2101596c9ceaf73ee5aaa -->

# TRUSTED\_CERTIFICATES\_FILE Option for Data Lake Relational Engine

Specifies the trust relationship for outbound Transport Layer Security \(TLS\) connections made by LDAP User Authentication, INC, and MIPC connections.



<a name="loioa3de3db284f2101596c9ceaf73ee5aaa__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa3de3db284f2101596c9ceaf73ee5aaa__iq_refso_699"/>

## Default

NULL, meaning that no outbound TLS connection can be started because there are no trusted certificate authorities.



<a name="loioa3de3db284f2101596c9ceaf73ee5aaa__iq_refso_701"/>

## Remarks

This option identifies the path to the location of the list of trusted certificate authorities. The list must be stored in a TXT file.

