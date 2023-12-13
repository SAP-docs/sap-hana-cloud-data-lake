<!-- loioa663018d84f210159ebca747f3b93a2a -->

# TEMP\_SPACE\_LIMIT\_CHECK Option for Data Lake Relational Engine

Checks for catalog store temporary space on a per connection basis.



<a name="loioa663018d84f210159ebca747f3b93a2a__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa663018d84f210159ebca747f3b93a2a__iq_refso_1048"/>

## Default

ON



<a name="loioa663018d84f210159ebca747f3b93a2a__iq_refso_1050"/>

## Remarks

When TEMP\_SPACE\_LIMIT\_CHECK is ON, the database server checks the amount of catalog store temporary file space that a connection uses. If a connection requests more than its quota of temporary file space, the request fails and the error “***Temporary space limit exceeded***” is returned.

Two factors are used to determine the temporary file quota for a connection: the maximum size of the temporary file, and the number of active database connections. The maximum size of the temporary file is the sum of the current size of the file and the amount of space available on the partition containing the file. When limit checking is turned on, the server checks a connection for exceeding its quota when the temporary file has grown to 80% or more of its maximum size, and the connection requests more temporary file space. Once this happens, any connection fails that uses more than the maximum temporary file space divided by the number of active connections.

> ### Note:  
> This option is unrelated to IQ temporary store space. To constrain the growth of IQ temporary space, use the QUERY\_TEMP\_SPACE\_LIMIT option and MAX\_TEMP\_SPACE\_PER\_CONNECTION option.

You can obtain information about the space available for the temporary file using the sa\_disk\_free\_space system procedure.

