<!-- loio3be134b96c5f10148030a559a29433ca -->

# Prefetches

Prefetching assists performance by cutting down on client/server round trips, and increases throughput by making many rows available without a separate request to the server for each row or block of rows.

Prefetches and multiple-row fetches are different. Prefetches can be carried out without explicit instructions from the client application. Prefetching retrieves rows from the server into a buffer on the client side, but does not make those rows available to the client application until the application fetches the appropriate row.

By default, the client library prefetches multiple rows whenever an application fetches a single row. The client library stores the additional rows in a buffer.



## Controlling Prefetching from an Application

-   The prefetch option controls whether prefetching occurs. You can set the prefetch option to Always, Conditional, or Off for a single connection. By default, it is set to Conditional.

-   In Embedded SQL, you can control prefetching on a per-cursor basis when you open a cursor on an individual FETCH operation using the BLOCK clause.

    The application can specify a maximum number of rows contained in a single fetch from the server by specifying the BLOCK clause. For example, if you are fetching and displaying 5 rows at a time, you could use BLOCK 5. Specifying BLOCK 0 fetches 1 record at a time and also causes a FETCH RELATIVE 0 to always fetch the row from the server again.

    Although you can also turn off prefetch by setting a connection parameter on the application, it is more efficient to specify BLOCK 0 than to set the prefetch option to Off.

-   Prefetch is disabled by default for value sensitive cursor types.

-   In Open Client, you can control prefetching behavior using ct\_cursor with CS\_CURSOR\_ROWS after the cursor is declared, but before it is opened.


Prefetch dynamically increases the number of prefetch rows when improvements in performance could be achieved. This includes cursors that meet the following conditions:

-   They use one of the supported cursor types:

    ODBC and OLE DB
    :   FORWARD-ONLY and READ-ONLY \(default\) cursors

    Embedded SQL
    :   DYNAMIC SCROLL \(default\), NO SCROLL, and INSENSITIVE cursors

    ADO.NET
    :   all cursors

-   They perform only FETCH NEXT operations \(no absolute, relative, or backward fetching\).

-   The application does not change the host variable type between fetches and does not use a GET DATA statement to get column data in chunks \(using *one* GET DATA statement to get the value is supported\).


