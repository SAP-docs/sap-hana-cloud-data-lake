<!-- loioa622ae5f84f21015bc6ddcb8796e03c9 -->

# READ Statement \[Interactive SQL\] for Data Lake Relational Engine

Reads Interactive SQL \(`dbisql`\) statements from a file.



<a name="loioa622ae5f84f21015bc6ddcb8796e03c9__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
READ [ ENCODING <encoding> ] <filename> [ <parameter> ] …;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa622ae5f84f21015bc6ddcb8796e03c9__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

ENCODING

</b></dt>
<dd>

An identifier or string that specifies encoding that is used to read the file.

The `READ` statement does not process escape characters when it reads a file. It assumes that the entire file is in the specified encoding. When running Interactive SQL, the encoding that is used to read the data is determined in the following order:

1.  The encoding specified by the ENCODING clause, if used.
2.  The encoding specified by the byte order mark \(BOM\) in the file, if used.
3.  The encoding specified with the default\_isql\_encoding option, if used.
4.  The default encoding for the platform you are running on.



</dd><dt><b>

*<filename\>*

</b></dt>
<dd>

If *<filename\>* has no file extension, Interactive SQL searches for the same file name with the extension `.sql`.

If *<filename\>* does not contain an absolute path, Interactive SQL searches for the file. The location of *<filename\>* is based on the location of the READ statement, as follows:

-   If the READ statement is executed directly in Interactive SQL, Interactive SQL first attempts to resolve the path to *<filename\>* relative to the directory in which Interactive SQL is running. If unsuccessful, Interactive SQL looks for *<filename\>* in the directories specified in the environment variable SQLPATH, then the directories specified in the environment variable PATH.
-   If the READ statements reside in an external file \(for example, a `.sql` file\), Interactive SQL first attempts to resolve the path to *<filename\>* relative to the location of the external file. If unsuccessful, Interactive SQL looks for *<filename\>* in a path relative to the directory in which Interactive SQL is running. If still unsuccessful, Interactive SQL looks in the directories specified in the environment variable SQLPATH, then the directories specified in the environment variable PATH.



</dd><dt><b>

*<parameter\>*

</b></dt>
<dd>

Can be listed after the name of the SQL script file, and correspond to the parameters named in the PARAMETERS statement at the beginning of the statement file.

Parameter names must be enclosed in square brackets. Interactive SQL substitutes the corresponding parameter wherever the source file contains <code>{ <i class="varname">&lt;parameter-name&gt;</i> }</code>.

The parameters passed to a script file can be identifiers, numbers, quoted identifiers, or strings. Any quotes around a parameter are placed into the text during the substitution. Parameters that are not identifiers, numbers, or strings \(contain spaces or tabs\) must be enclosed in square brackets \(\[ \]\). This allows for arbitrary textual substitution in the script file.

If not enough parameters are passed to the script file, Interactive SQL prompts for values for the missing parameters.

When executing a `reload.sql` file with Interactive SQL, you must specify the encryption key as a parameter. If you do not provide the key in the READ statement, Interactive SQL prompts for the key.



</dd>
</dl>



<a name="loioa622ae5f84f21015bc6ddcb8796e03c9__IQ_Permissions"/>

## Privileges

None



<a name="loioa622ae5f84f21015bc6ddcb8796e03c9__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not applicable



<a name="loioa622ae5f84f21015bc6ddcb8796e03c9__IQ_Examples"/>

## Examples

-   The following example reads from the file `status.rpt` and `birthday.sql` and passes the parameter values to the variables within the file:

    ```
    READ status.rpt '160';
    ```

    ```
    READ birthday.sql [>= '1988-1-1'] [<= '1988-1-30'];
    ```

-   The following example uses the PARAMETERS clause to pass parameters to a script file:

    ```
    [test1.sql]
    PARAMETERS par1, par2;
    
    BEGIN
    DECLARE v_par1 int;
    DECLARE v_par2 varchar(200)
    
    SET v_par1 = {par1};
    SET v_par2 = {par2};
    
    MESSAGE STRING('PAR1 Value: ', v_par1 ) TO CLIENT;
    MESSAGE STRING('PAR2 Value: ', v_par2 ) TO CLIENT;
    
    END;
    ```

    ```
    (USR1)> READ test1.sql 123 '041028'
    PAR1 Value: 123
    PAR2 Value: 041028;
    ```

    > ### Note:  
    > You must enclose the second parameter value 041028 in quotes, as *<v\_par2\>* is declared as a character data type.


**Related Information**  


[DEFAULT\_ISQL\_ENCODING Option \[Interactive SQL\] for Data Lake Relational Engine](../090-database-options/default-isql-encoding-option-interactive-sql-for-data-lake-relational-engine-a63407d.md "Specifies the code page used by READ and OUTPUT statements.")

[PARAMETERS Statement \[Interactive SQL\] for Data Lake Relational Engine](parameters-statement-interactive-sql-for-data-lake-relational-engine-a621ba2.md "Specifies parameters to an Interactive SQL (dbisql) command file.")

