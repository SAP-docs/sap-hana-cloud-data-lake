<!-- loio8175eb2b6ce2101490f9eaa998519272 -->

# sa\_http\_header\_info System Procedure for Data Lake Relational Engine

Returns HTTP request header names and values.



<a name="loio8175eb2b6ce2101490f9eaa998519272__section_idn_b13_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_http_header_info( [<header_parm>] );
```



## Parameters


<dl>
<dt><b>

*<header\_parm\>* 

</b></dt>
<dd>

Use this optional VARCHAR\(255\) parameter to specify an HTTP header name. The default is NULL.



</dd>
</dl>



## Result Set


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Name

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

The HTTP header name.

</td>
</tr>
<tr>
<td valign="top">

Value

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

The HTTP header value.

</td>
</tr>
</table>



## Remarks

The sa\_http\_header\_info system procedure returns header names and values. If you do not specify the header name using the optional parameter, the result set contains values for all headers.

This procedure returns a non-empty result set if it is called while processing an HTTP request within a web service.

> ### Note:  
> The sa\_http\_header\_info system procedure may return multiple rows with the same name if the request contains multiple HTTP headers with the same name.



## Privileges

Requires EXECUTE object-level privilege on the procedure.



## Side Effects

None



## Examples

The following web service procedure which is called from a web service illustrates the use of the sa\_http\_header\_info system procedure.

```
CREATE OR REPLACE PROCEDURE User1.HTTPHeaderExample()
RESULT ( html_string LONG VARCHAR )
BEGIN
    DECLARE myname VARCHAR(255);
    DECLARE myvalue LONG VARCHAR;
    DECLARE err_notfound
        EXCEPTION FOR SQLSTATE '02000';
    DECLARE curs CURSOR FOR 
        SELECT Name, Value FROM sa_http_header_info();
    MESSAGE '=== HTTP Headers ===' TO CONSOLE;
    OPEN curs;
    FetchLoop: LOOP
        FETCH next curs INTO myname, myvalue;
        IF SQLSTATE = err_notfound THEN
            LEAVE FetchLoop;
        END IF;
        MESSAGE myname, '=', myvalue TO CONSOLE;
    END LOOP FetchLoop;
    CLOSE curs;
END;
```

When the web service that calls this web service procedure is used, output appears in the database server messages window that is similar to the following.

```
=== HTTP Headers ===
@HttpQueryString=param1=value1&param2=value2&param3=value3
User-Agent=Mozilla/5.0 (Windows NT 6.1; WOW64; rv:16.0) Gecko/20100101 Firefox/16.0
Authorization=Basic VXNlcjE6dXNlcg==
Cache-Control=max-age=0
Connection=keep-alive
Host=webserver-t3500.sap.com:8082
@HttpURI=/ShowHTTPHeaders?param1=value1&param2=value2&param3=value3
@HttpMethod=GET
Accept=text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
@HttpVersion=HTTP/1.1
Accept-Language=en-US,en;q=0.5
Accept-Encoding=gzip, deflate
```

