<!-- loioa525ca8584f2101587e5cda86e1446a8 -->

# Conversion Between BIT and VARCHAR Data Types in Data Lake Relational Engine

Data lake Relational Engine supports implicit conversion between BIT and CHAR, and BIT and VARCHAR data types for comparison operators, arithmetic operations, and INSERT and UPDATE statements



Using the following tables and data, these examples illustrate both implicit and explicit conversions between BIT and CHAR, and BIT and VARCHAR data types:

```
CREATE TABLE tchar(c1 CHAR(9))
CREATE TABLE tvarchar(c2 VARCHAR(9))
CREATE TABLE tbar(c2 BIT)
CREATE TABLE tbit(c2 BIT)

INSERT tbar VALUES(1)
INSERT tbar VALUES(0)
```

-   Implicit conversion of BIT to VARCHAR / VARCHAR to BIT and implicit conversion of BIT to VARCHAR:

    ```
    INSERT tvarchar SELECT c2 FROM tbar
    SELECT c2, char_length(c2) FROM tvarchar
    
    c2,char_length(tvarchar.c2)
    ---------------------------
    '1',1
    '0',1
    ```

-   Implicit conversion of VARCHAR to BIT:

    ```
    INSERT tbit SELECT c2 FROM tvarchar
    SELECT c2 FROM tbit
    
    c2
    --
    0
    1
    ```

-   Explicit conversion of BIT to CHAR / CHAR to BIT and explicit conversion of BIT to CHAR:

    ```
    INSERT tchar SELECT CONVERT (CHAR(9), c2) FROM tbar
    SELECT c1, char_length(c1) FROM tchar
    
    c1,char_length(tchar.c1)
    ------------------------
    '1',9
    '0',9
    ```

-   Explicit conversion of CHAR to BIT:

    ```
    INSERT tbit SELECT CONVERT (BIT, c1) FROM tchar
    SELECT c2 FROM tbit
    
    c2
    --
    0
    1
    ```

-   Explicit conversion of BIT to VARCHAR / VARCHAR to BIT and explicit conversion of BIT to VARCHAR:

    ```
    INSERT tvarchar SELECT CONVERT(VARCHAR(9), c2)
      FROM tbar
    SELECT c2, char_length(c2) FROM tvarchar
    
    c2,char_length(tvarchar.c2)
    ---------------------------
    '1',1
    '0',1
    ```

-   Explicit conversion of VARCHAR to BIT:

    ```
    INSERT tbit SELECT CONVERT (BIT, c2) FROM tvarchar
    SELECT c2 FROM tbit
    
    c2
    --
    0
    1
    ```


