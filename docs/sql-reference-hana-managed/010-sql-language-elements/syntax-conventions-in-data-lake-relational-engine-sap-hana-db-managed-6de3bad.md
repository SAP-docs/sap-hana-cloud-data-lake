<!-- loio6de3badc6bd94e5e90e364bd505414c6 -->

# Syntax Conventions in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Conventions used in data lake Relational Engine SQL syntax descriptions.



 Keywords
 :   All SQL keywords appear in UPPERCASE; however, SQL keywords are case-insensitive, so you can type keywords in any case. For example, SELECT is the same as Select, which is the same as select.

  Placeholders
 :   Items that must be replaced with appropriate identifiers or expressions are shown in *<italics\>*.

  Continuation
 :   Lines beginning with an ellipsis \( … \) are a continuation from the previous line.

  Optional portions
 :   Optional portions of a statement are enclosed by square brackets. For example:

    ```
    RELEASE SAVEPOINT [ savepoint-name ]
    ```

    This example indicates that the *<savepoint-name\>* is optional. Don’t type the square brackets.

  Repeating items
 :   Lists of repeating items are shown with an element of the list followed by an ellipsis. One or more list elements are allowed. When more than one is specified, they must be separated by commas if indicated as such. For example:

    ```
    UNIQUE ( column-name [ , ... ] )
    ```

    The example indicates that you can specify *<column-name\>* more than once, separated by commas. Don’t type the square brackets.

  Alternatives
 :   When one option must be chosen, the alternatives are enclosed in curly braces. For example:

    ```
    [ QUOTES { ON | OFF } ] 
    ```

    The example indicates that if you choose the QUOTES option, you must provide one of ON or OFF. Don’t type the curly braces or the square brackets.

  One or more options
 :   If you specify more than one option, then separate your choices with commas. For example:

    ```
    { CONNECT, DBA, RESOURCE }
    ```

 