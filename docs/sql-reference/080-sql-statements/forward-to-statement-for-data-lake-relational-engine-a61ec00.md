<!-- loioa61ec00b84f210158c6dee868f166997 -->

# FORWARD TO Statement for Data Lake Relational Engine

Sends native syntax to a remote server, enabling users to specify the server to which a passthrough connection is required.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<dl>
<dt><b>

Syntax 1 – Sends a Statement to a Remote Server

</b></dt>
<dd>

```
FORWARD TO <server-name> { <sql-statement> } 
```



</dd><dt><b>

Syntax 2 – Places Data Lake Relational Engine into Passthrough Mode to Send a Series of Statements to a Remote Server

</b></dt>
<dd>

```
FORWARD TO [ <server-name> ]
```



</dd>
</dl>



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



## Parameters


<dl>
<dt><b>

*<server-name\>*

</b></dt>
<dd>

The name of the remote server.



</dd><dt><b>

*<sql-statement\>*

</b></dt>
<dd>

A command in the native syntax of the remote server. The command or group of commands is enclosed in curly braces \(`{}`\) or single quotes.



</dd>
</dl>



<a name="loioa61ec00b84f210158c6dee868f166997__IQ_Usage"/>

## Remarks

If you specify a *<server-name\>*, but do not specify a statement in the FORWARD TO query, your session enters passthrough mode, and all subsequent queries are passed directly to the remote server. To turn passthrough mode OFF, issue the FORWARD TO statement without a *<server\_name\>* specification.

> ### Note:  
> The FORWARD TO statement is a server directive and cannot be used in stored procedures, triggers, events, or batches.

FORWARD TO enables users to specify the server to which a passthrough connection is required. The statement can be used:

-   To send a statement to a remote server \(Syntax 1\)
-   To place data lake Relational Engine into passthrough mode for sending a series of statements to a remote server \(Syntax 2\)

When establishing a connection to *<server-name\>* on behalf of the user, the server uses:

-   A remote login alias set using CREATE EXTERNLOGIN
-   If a remote login alias is not set up, the name and password used to communicate with data lake Relational Engine

If the connection cannot be made to the server specified, the reason is contained in a message returned to the user.

After statements are passed to the requested server, any results are converted into a form that can be recognized by the client program.



<a name="loioa61ec00b84f210158c6dee868f166997__IQ_Permissions"/>

## Privileges

None



<a name="loioa61ec00b84f210158c6dee868f166997__IQ_Side_Effects"/>

## Side Effects

The remote connection is set to AUTOCOMMIT mode for the duration of the FORWARD TO session. Any work that was pending prior to the FORWARD TO statement is automatically committed.



<a name="loioa61ec00b84f210158c6dee868f166997__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by Open Client/Open Server



<a name="loioa61ec00b84f210158c6dee868f166997__IQ_Examples"/>

## Examples

The following example shows a passthrough session with the remote server abcprod:

```
FORWARD TO abcprod
SELECT * from titles
SELECT * from authors
FORWARD TO
```

**Related Information**  


[CREATE SERVER Statement for Data Lake Relational Engine](create-server-statement-for-data-lake-relational-engine-a619187.md "Creates a remote server.")

