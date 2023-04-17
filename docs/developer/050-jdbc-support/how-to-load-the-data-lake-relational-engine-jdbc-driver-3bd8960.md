<!-- loio3bd896036c5f101489c4ea2fec763545 -->

# How to Load the Data Lake Relational Engine JDBC Driver

Ensure that the JDBC driver is in your class file path.

```
set classpath=%IQDIR17%\java\sajdbc4.jar;%classpath%
```

The JDBC driver takes advantage of the new automatic driver registration. The driver is automatically loaded at execution startup when it is in the class file path.



## Required Files

The Java component of the JDBC driver is included in the `sajdbc4.jar` file installed into the `Java` subdirectory of your SAP HANA Data Lake Client installation.

For Windows, the native component is <code>dbjdbc<i>17</i>.dll</code> in the `Bin64` subdirectory of your SAP HANA Data Lake Client installation.

For UNIX and Linux, the native component is <code>libdbjdbc<i>17</i>.so</code>. This component must be in the system path.

