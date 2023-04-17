<!-- loioa248fa2184f21015ba00f6e8d43ec7f1 -->

# sp\_iqmpxdumptlvlog Procedure for Data Lake Relational Engine

Returns the contents of the table version log in a readable format.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqmpxdumptlvlog [main], [asc | desc]
```



<a name="loioa248fa2184f21015ba00f6e8d43ec7f1__iq_iqmpx_254"/>

## Remarks

`sp_iqmpxdumptlvlog` returns the contents of the queue through which the coordinator propagates DML and DDL commands to worker nodes.

The `asc` or `desc` arguments specify the row order. These arguments require the `main` argument. The default options are:

```
'main', 'asc'
```



<a name="loioa248fa2184f21015ba00f6e8d43ec7f1__iq_iqmpx_253"/>

## Privileges

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md). 



## Side Effects

None



## Example

The following shows sample output from `sp_iqmpxdumptlvlog`:

```
RowID     Contents
--------------------------------------------------------------
1         Txn CatId:196 CmtId:196 TxnId:195 Last Rec:1 
          UpdateTime: 2011-08-08 15:41:43.621
2         Txn CatId:243 CmtId:243 TxnId:242 Last Rec:5 
          UpdateTime: 2011-08-08 15:42:25.070
3         DDL: Type=34, CatID=0, IdxID=0,
          Object=IQ_SYSTEM_TEMP, Owner=mpx4022_w1
4         CONN: CatID=0, ConnUser=
5         SQL: ALTER DBSPACE "IQ_SYSTEM_TEMP" ADD FILE
          "w1_temp1" '/dev/raw/raw25' FILE ID 16391 PREFIX 65536 
          FINISH 0 FIRST BLOCK
1         BLOCK COUNT 3276792 RESERVE 0 MULTIPLEX SERVER 
          "mpx4022_w1" COMMITID 242 CREATETIME 
          '2011-08-08 15:42:24.860'
6         Txn CatId:283 CmtId:283 TxnId:282 Last Rec:7 
          UpdateTime: 2011-08-08 15:42:50.827
7         RFRB TxnID: 242 CmtID:243 ServerID 0 BlkmapID:
          0d00000000000000d2000a000000000002000000000000000000
          0000000000000000000008003501010000000c38000000000000
          010000000000000000000000RFID:01000501000000001300000
          0000000000100000000000100RBID:010005010000000013000
```

