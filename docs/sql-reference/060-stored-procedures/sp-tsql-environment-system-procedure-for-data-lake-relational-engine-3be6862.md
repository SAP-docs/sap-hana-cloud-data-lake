<!-- loio3be686266c5f1014ad21c9c116ab5a77 -->

# sp\_tsql\_environment System Procedure for Data Lake Relational Engine

Sets connection options when users connect from jConnect or Open Client applications.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_tsql_environment( )
```



## Remarks

The sp\_login\_environment procedure is the default procedure specified by the login\_procedure database option. For each new connection, the procedure specified by login\_procedure is called. If the connection uses the TDS communications protocol \(that is, if it is an Open Client or jConnect connection\), then sp\_login\_environment in turn calls sp\_tsql\_environment.

This procedure sets database options so that they are compatible with default Adaptive Server Enterprise behavior.

To change the default behavior, create new procedures and alter your login\_procedure option to point to these new procedures.

Below is the list of the options set by sp\_tsql\_environment procedure:

```
if db_property( 'IQStore' ) = 'Off' then
    -- SAP IQ datastore
    SET TEMPORARY OPTION close_on_endtrans='OFF';
end if;
SET TEMPORARY OPTION ansinull='OFF';
SET TEMPORARY OPTION tsql_variables='ON';
SET TEMPORARY OPTION ansi_blanks='ON';
SET TEMPORARY OPTION chained='OFF';
SET TEMPORARY OPTION quoted_identifier='OFF';
SET TEMPORARY OPTION allow_nulls_by_default='OFF';
SET TEMPORARY OPTION on_tsql_error='CONTINUE';
SET TEMPORARY OPTION isolation_level='1';
SET TEMPORARY OPTION date_format='YYYY-MM-DD';
SET TEMPORARY OPTION timestamp_format='YYYY-MM-DD HH:NN:SS.SSS';
SET TEMPORARY OPTION time_format='HH:NN:SS.SSS';
SET TEMPORARY OPTION date_order='MDY';
SET TEMPORARY OPTION escape_character='OFF';
```



## Privileges

You need to have the EXECUTE privilege on the system procedure.



## Side Effects

None



The example below calls the sp\_tsql\_environment procedure:

```
CALL dbo.sp_tsql_environment();
```

