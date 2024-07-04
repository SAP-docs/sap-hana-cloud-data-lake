<!-- loioa48026b384f2101598ebdc87a2fbefd9 -->

# sp\_iqsysmon System Procedure Examples With Output for Data Lake Relational Engine

The sp\_iqsysmon examples here show output information.



<a name="loioa48026b384f2101598ebdc87a2fbefd9__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa48026b384f2101598ebdc87a2fbefd9__iq_refbb_1793"/>

## Example 1

The following example displays output for the Buffer Allocation \(Main and Temporary\) after 20 minutes:

```
sp_iqsysmon '00:20:00', 'mbufalloc tbufalloc';
```

```
==============================
Buffer Allocator (Main)"
==============================

STATS-NAME                  VALUE
NActiveCommands                 2
BufAllocMaxBufs              2275( 81.6% )
BufAllocAvailBufs            2115( 93.0% )
BufAllocReserved              160( 7.0% )
BufAllocAvailPF               750( 33.0% )
BufAllocSlots                 100
BufAllocNPinUsers               0
BufAllocNPFUsers                2
BufAllocNPostedUsrs             0
BufAllocNUnpostUsrs             0
BufAllocPinQuota                0
BufAllocNPostEst                0
BufAllocNUnPostEst              0
BufAllocMutexLocks              0
BufAllocMutexWaits              0( 0.0% )

STATS-NAME                  VALUE
NActiveCommands                 2
BufAllocMaxBufs              2275( 81.6% )
BufAllocAvailBufs            2115( 93.0% )
BufAllocReserved              160( 7.0% )
BufAllocAvailPF               750( 33.0% )
BufAllocSlots                 100
BufAllocNPinUsers               0
BufAllocNPFUsers                2
BufAllocNPostedUsrs             0
BufAllocNUnpostUsrs             0
BufAllocPinQuota                0
BufAllocNPostEst                0
BufAllocNUnPostEst              0
BufAllocMutexLocks              0
BufAllocMutexWaits              0( 0.0% )	

STATS-NAME              TOTAL UNKNWN HASH CSORT  ROW ROWCOL  FP GARRAY LOB BTREE   BM   BV STORE  TEST
NumClients                  2      0    0     0    2      0   0      0   0     0    0    0     0     0
PinUserQuota                0      0    0     0    0      0   0      0   0     0    0    0     0     0
PrefetchUserQuota         160      0    0     0  160      0   0      0   0     0    0    0     0     0
PinUserRegisters            2      2    0     0    0      0   0      0   0     0    0    0     0     0
PfUserRegisters          4697      0    0     0  382   2621 377    182   0     2    0    0     0     0

ClientCountOfPinners        0      1    3     6   10     33  66    100 333   666 1000 3333  6666 10000
Unknown                     0      0    0     0    0      0   0      0   0     0    0    0     0     0
Hash                        0      0    0     0    0      0   0      0   0     0    0    0     0     0
Sort                        0      0    0     0    0      0   0      0   0     0    0    0     0     0
Row                         2      0    0     0    0      0   0      0   0     0    0    0     0     0
RowColumn                   0      0    0     0    0      0   0      0   0     0    0    0     0     0
FP                          0      0    0     0    0      0   0      0   0     0    0    0     0     0
Garray                      0      0    0     0    0      0   0      0   0     0    0    0     0     0
LOB                         0      0    0     0    0      0   0      0   0     0    0    0     0     0
BTree                       0      0    0     0    0      0   0      0   0     0    0    0     0     0
BM                          0      0    0     0    0      0   0      0   0     0    0    0     0     0
BV                          0      0    0     0    0      0   0      0   0     0    0    0     0     0
Store                       0      0    0     0    0      0   0      0   0     0    0    0     0     0
Test                        0      0    0     0    0      0   0      0   0     0    0    0     0     0
DBCC                        0      0    0     0    0      0   0      0   0     0    0    0     0     0
Unknown                     0      0    0     0    0      0   0      0   0     0    0    0     0     0
Unknown                     0      0    0     0    0      0   0      0   0     0    0    0     0     0
Run                         0      0    0     0    0      0   0      0   0     0    0    0     0     0
QCPRun                      0      0    0     0    0      0   0      0   0     0    0    0     0     0
TextDoc                     0      0    0     0    0      0   0      0   0     0    0    0     0     0
Unknown                     0      0    0     0    0      0   0      0   0     0    0    0     0     0
Unknown                     0      0    0     0    0      0   0      0   0     0    0    0     0     0
VDO                         0      0    0     0    0      0   0      0   0     0    0    0     0     0
Load                     Pass      2    0     0    0      0   0      0   0     0    0    0     0     0

STATS-NAME (cont'd       DBCC BLKMAP IQUTIL
NumClients                  0      0    0    0    0       0   0       0    0      0
PinUserQuota                0      0    0    0    0       0   0       0    0      0
PrefetchUserQuota           0      0    0    0    0       0   0       0    0      0
PinUserRegisters            0      0    0    0    0       0   0       0    0      0
PfUserRegisters             0      0    0    0    0       0   0       0 1133      0

ClientCountOfPinners    33333  66666  100000  4294967295
Unknown                     0      0       0           0
Hash                        0      0       0           0
Sort                        0      0       0           0
Row                         0      0       0           0
RowColumn                   0      0       0           0
FP                          0      0       0           0
Garray                      0      0       0           0
LOB                         0      0       0           0
BTree                       0      0       0           0
BM                          0      0       0           0
BV                          0      0       0           0
Store                       0      0       0           0
Test                        0      0       0           0
DBCC                        0      0       0           0
Unknown                     0      0       0           0
Unknown                     0      0       0           0
Run                         0      0       0           0
QCPRun                      0      0       0           0
TextDoc                     0      0       0           0
Unknown                     0      0       0           0
Unknown                     0      0       0           0
VDO                         0      0       0           0
Load                        0      0       0           0       0       0


==============================
Buffer Allocator (Temporary)
==============================

STATS-NAME              VALUE
NActiveCommands             2
BufAllocMaxBufs          2275( 81.6% )
BufAllocAvailBufs        2263( 99.5% )
BufAllocReserved           12( 0.5% )
BufAllocAvailPF           908( 39.9% )
BufAllocSlots             100
BufAllocNPinUsers           2
BufAllocNPFUsers            2
BufAllocNPostedUsrs         0
BufAllocNUnpostUsrs         0
BufAllocPinQuota          175
BufAllocNPostEst            2
BufAllocNUnPostEst          2
BufAllocMutexLocks          0
BufAllocMutexWaits          0( 0.0% )

STATS-NAME              TOTAL UNKNWN HASH CSORT  ROW ROWCOL  FP  GARRAY  LOB  BTREE    BM    BV  STORE   TEST
NumClients                  4      0    0     4    0      0   0       0    0      0     0     0      0      0
PinUserQuota               10      0    0    10    0      0   0       0    0      0     0     0      0      0
PrefetchUserQuota           2      0    0     2    0      0   0       0    0      0     0     0      0      0
PinUserRegisters          668      0  300   247    0      0   0       0    0      0     0     0      0      0
PfUserRegisters           675      0    0   295    0      0   0       0    0      0     0     0      1      0

ClientCountOfPinners        0      1    3     6   10     33  66     100  333    666  1000  3333   6666  10000
Unknown                     0      0    0     0    0      0   0       0    0      0     0     0      0      0
Hash                        0      0    0     0    0      0   0       0    0      0     0     0      0      0
Sort                        2      0    1     0    1      0   0       0    0      0     0     0      0      0
Row                         0      0    0     0    0      0   0       0    0      0     0     0      0      0
RowColumn                   0      0    0     0    0      0   0       0    0      0     0     0      0      0
FP                          0      0    0     0    0      0   0       0    0      0     0     0      0      0
Garray                      0      0    0     0    0      0   0       0    0      0     0     0      0      0
LOB                         0      0    0     0    0      0   0       0    0      0     0     0      0      0
BTree                       0      0    0     0    0      0   0       0    0      0     0     0      0      0
BM                          0      0    0     0    0      0   0       0    0      0     0     0      0      0
BV                          0      0    0     0    0      0   0       0    0      0     0     0      0      0
Store                       0      0    0     0    0      0   0       0    0      0     0     0      0      0
Test                        0      0    0     0    0      0   0       0    0      0     0     0      0      0
DBCC                        0      0    0     0    0      0   0       0    0      0     0     0      0      0
Unknown                     0      0    0     0    0      0   0       0    0      0     0     0      0      0
Unknown                     0      0    0     0    0      0   0       0    0      0     0     0      0      0
Run                         0      0    0     0    0      0   0       0    0      0     0     0      0      0
QCPRun                      0      0    0     0    0      0   0       0    0      0     0     0      0      0
TextDoc                     0      0    0     0    0      0   0       0    0      0     0     0      0      0
Unknown                     0      0    0     0    0      0   0       0    0      0     0     0      0      0
Unknown                     0      0    0     0    0      0   0       0    0      0     0     0      0      0
VDO                         0      0    0     0    0      0   0       0    0      0     0     0      0      0
Load                     Pass      2    0     0    0      0   0       0    0      0     0     0      0      0

STATS-NAME (cont'd)      DBCC BLKMAP IQUTIL
NumClients                  0      0      0    0   0      0   0       0    0      0
PinUserQuota                0      0      0    0   0      0   0       0    0      0
PrefetchUserQuota           0      0      0    0   0      0   0       0    0      0
PinUserRegisters            0      0      0  110   2      0   0       0    0      9
PfUserRegisters             0      0      0  378   0      0   0       1    0      0

ClientCountOfPinners    33333  66666  100000   4294967295
Unknown                     0      0       0            0
Hash                        0      0       0            0
Sort                        0      0       0            0
Row                         0      0       0            0
RowColumn                   0      0       0            0
FP                          0      0       0            0
Garray                      0      0       0            0
LOB                         0      0       0            0
BTree                       0      0       0            0
BM                          0      0       0            0
BV                          0      0       0            0
Store                       0      0       0            0
Test                        0      0       0            0
DBCC                        0      0       0            0
Unknown                     0      0       0            0
Unknown                     0      0       0            0
Run                         0      0       0            0
QCPRun                      0      0       0            0
TextDoc                     0      0       0            0
Unknown                     0      0       0            0
Unknown                     0      0       0            0
VDO                         0      0       0            0
Load                        0      0       0            0       0       0
```



<a name="loioa48026b384f2101598ebdc87a2fbefd9__section_pd3_lkf_nbb"/>

## Example 2

The following example displays output for the Buffer Manager \(Main and Temporary\) after 20 minutes:

```
sp_iqsysmon '00:20:00', 'mbufman tbufman';
```

```
==============================
Buffer Manager (Main)
==============================

STATS-NAME            TOTAL   NONE TXTPOS TXTDOC CMPACT BTREEV BTREEF  BV   VDO DBEXT DBID SORT STORE GARRAY
Finds                 80137      0      0      0      0   9046   3307   0 20829     0    0    0     0    275
Hits                  80090      0      0      0      0   9015   3291   0 20829     0    0    0     0    275
Hit%                   99.9      0      0      0      0   99.7   99.5   0   100     0    0    0     0    100
FalseMiss             26469      0      0      0      0     63     40   0  1097     0    0    0     0      0
UnOwnRR                  48      0      0      0      0     31     16   0     1     0    0    0     0      0
Cloned                    0      0      0      0      0      0      0   0     0     0    0    0     0      0
Creates                1557      0      0      0      0     60    179   0   256     0    0    0     0     58
Destroys                546      0      0      0      0     12     21   0     6     0    0    0     0     29
Dirties                7554      0      0      0      0   1578    585   0     0     0    0    0     0      0
RealDirties            2254      0      0      0      0    117    180   0   542     0    0    0     0     58
PrefetchReqs             80      0      0      0      0      0      0   0    74     0    0    0     0      0
PrefetchNotInMem          1      0      0      0      0      0      0   0     1     0    0    0     0      0
PrefetchInMem          1466      0      0      0      0      0      0   0  1466     0    0    0     0      0
Reads                    48      0      0      0      0     31     16   0     1     0    0    0     0      0
PReadBlks               114      0      0      0      0     80     32   0     2     0    0    0     0      0
PReadKB                   0      0      0      0      0      0      0   0     0     0    0    0     0      0
ReReads                   0      0      0      0      0      0      0   0     0     0    0    0     0      0
Writes                 2002      0      0      0      0    104    163   0   538     0    0    0     0     29
PWriteBlks             6506      0      0      0      0    210    326   0  1115     0    0    0     0     58
PWriteKB                  0      0      0      0      0      0      0   0     0     0    0    0     0      0
GrabbedDirty              0      0      0      0      0      0      0   0     0     0    0    0     0      0
ReadRemoteRpc             0      0      0      0      0      0      0   0     0     0    0    0     0      0
ReadRemotePhyIO           0      0      0      0      0      0      0   0     0     0    0    0     0      0

STATS-NAME (cont'd)  BARRAY BLKMAP   HASH   CKPT     BM   TEST   CMID RIDCA   LOB LVCRID FILE RIDMAP RVLOG
Finds                  2681   8329      0      0  35670      0      0     0     0      0    0      0     0
Hits                   2681   8329      0      0  35670      0      0     0     0      0    0      0     0
Hit%                    100    100      0      0    100      0      0     0     0      0    0      0     0
FalseMiss                84   8329      0      0  16856      0      0     0     0      0    0      0     0
UnOwnRR                   0      0      0      0      0      0      0     0     0      0    0      0     0
Cloned                    0      0      0      0      0      0      0     0     0      0    0      0     0
Creates                 108    358      0      0    538      0      0     0     0      0    0      0     0
Destroys                  0    126      0      0     59      0      0     0     0      0    0      0     0
Dirties                 512    235      0      0   4644      0      0     0     0      0    0      0     0
RealDirties             128    593      0      0    636      0      0     0     0      0    0      0     0
PrefetchReqs              6      0      0      0      0      0      0     0     0      0    0      0     0
PrefetchNotInMem          0      0      0      0      0      0      0     0     0      0    0      0     0
PrefetchInMem             0      0      0      0      0      0      0     0     0      0    0      0     0
Reads                     0      0      0      0      0      0      0     0     0      0    0      0     0
PReadBlks                 0      0      0      0      0      0      0     0     0      0    0      0     0
PReadKB                   0      0      0      0      0      0      0     0     0      0    0      0     0
ReReads                   0      0      0      0      0      0      0     0     0      0    0      0     0
Writes                  128    466      0      0    574      0      0     0     0      0    0      0     0
PWriteBlks              239   3728      0      0    830      0      0     0     0      0    0      0     0
PWriteKB                  0      0      0      0      0      0      0     0     0      0    0      0     0
GrabbedDirty              0      0      0      0      0      0      0     0     0      0    0      0     0
ReadRemoteRpc             0      0      0      0      0      0      0     0     0      0    0      0     0
ReadRemotePhyIO           0      0      0      0      0      0      0     0     0      0    0      0     0

STATS-NAME            VALUE
BusyWaits                98
LRUNumLocks          401784
LRUNumSpinsWoTO           0      0%
LRUNumSpinLoops        4315
LRUNumTimeOuts         4315  -1.10%
BmapHTNumLocks            0
BmapHTNumWaits            0      0%
CacheTeamTimesWoken     182
CacheTeamNumAsleep       10
BmapHTMaxEntries       4096
BmapHTNEntries           27
BmapHTNInserts        31954
BmapHTNCollisn          203
BmapHTNFinds          51419
BmapHTNHits           19576
BmapHTNHits1          19550
BmapHTNHits2             26
BmapHTNClears         31933
BmapHTNLChain             1
BmapHTNRehash             0
BlockmapMutexsNLocks      0
BlockmapMutexsNWaits      0
BlockmapUID            3659
BlockmapUIDnallocs     3652
BlockmapRegEver       31851
BlockmapRegisters     31844
BufHTNBuckets          4608
BufHTNEntries          1208
BufHTNw2orMore          158
BufHTMaxBucketSize       19
BufHTNFoiledOps           0
IONumLocks                0
IONumWaits                0      0%

==============================
Buffer Manager (Temporary)
==============================

STATS-NAME            TOTAL NONE TXTPOS TXTDOC CMPACT BTREEV BTREEF BV VDO DBEXT DBID  SORT STORE GARRAY
Finds                 31656    0      0      0      0      0      0  0   0     0    0  1022     0      0
Hits                  31655    0      0      0      0      0      0  0   0     0    0  1022     0      0
Hit%                    100    0      0      0      0      0      0  0   0     0    0   100     0      0
FalseMiss             23898    0      0      0      0      0      0  0   0     0    0     0     0      0
UnOwnRR                   0    0      0      0      0      0      0  0   0     0    0     0     0      0
Cloned                    0    0      0      0      0      0      0  0   0     0    0     0     0      0
Creates                5682    0      0      0      0      0      0  0   0     0    0  1048   716      0
Destroys               5670    0      0      0      0      0      0  0   0     0    0   821    17      0
Dirties                6702    0      0      0      0      0      0  0   0     0    0   379     0      0
RealDirties            5692    0      0      0      0      0      0  0   0     0    0  1048   716      0
PrefetchReqs              1    0      0      0      0      0      0  0   0     0    0     0     0      0
PrefetchNotInMem          1    0      0      0      0      0      0  0   0     0    0     0     0      0
PrefetchInMem           446    0      0      0      0      0      0  0   0     0    0   446     0      0
Reads                     2    0      0      0      0      0      0  0   0     0    0     0     0      0
PReadBlks              4096    0      0      0      0      0      0  0   0     0    0     0     0      0
PReadKB                   0    0      0      0      0      0      0  0   0     0    0     0     0      0
ReReads                   2    0      0      0      0      0      0  0   0     0    0     0     0      0
Writes                   10    0      0      0      0      0      0  0   0     0    0     0     0      0
PWriteBlks               80    0      0      0      0      0      0  0   0     0    0     0     0      0
PWriteKB                  0    0      0      0      0      0      0  0   0     0    0     0     0      0
GrabbedDirty              0    0      0      0      0      0      0  0   0     0    0     0     0      0
ReadRemoteRpc             0    0      0      0      0      0      0  0   0     0    0     0     0      0
ReadRemotePhyIO           0    0      0      0      0      0      0  0   0     0    0     0     0      0

STATS-NAME (cont'd)  BARRAY BLKMAP   HASH   CKPT    BM   TEST   CMID RIDCA   LOB LVCRID FILE RIDMAP RVLOG
Finds                     0   8569    124      0 21939      0      0     0     0      0    2      0     0
Hits                      0   8569    124      0 21939      0      0     0     0      0    1      0     0
Hit%                      0    100    100      0   100      0      0     0     0      0   50      0     0
FalseMiss                 0   8569      0      0 15328      0      0     0     0      0    1      0     0
UnOwnRR                   0      0      0      0     0      0      0     0     0      0    0      0     0
Cloned                    0      0      0      0     0      0      0     0     0      0    0      0     0
Creates                   0   1440    777      0  1041      0      0     0     0      0    0    660     0
Destroys                  0   1434    777      0   123      0      0     0     0      0    0    660     0
Dirties                   0      0      0      0  6323      0      0     0     0      0    0      0     0
RealDirties               0   1440    777      0  1051      0      0     0     0      0    0    660     0
PrefetchReqs              0      0      0      0     0      0      0     0     0      0    1      0     0
PrefetchNotInMem          0      0      0      0     0      0      0     0     0      0    1      0     0
PrefetchInMem             0      0      0      0     0      0      0     0     0      0    0      0     0
Reads                     0      0      0      0     0      0      0     0     0      0    2      0     0
PReadBlks                 0      0      0      0     0      0      0     0     0      0 4096      0     0
PReadKB                   0      0      0      0     0      0      0     0     0      0    0      0     0
ReReads                   0      0      0      0     0      0      0     0     0      0    2      0     0
Writes                    0      0      0      0    10      0      0     0     0      0    0      0     0
PWriteBlks                0      0      0      0    80      0      0     0     0      0    0      0     0
PWriteKB                  0      0      0      0     0      0      0     0     0      0    0      0     0
GrabbedDirty              0      0      0      0     0      0      0     0     0      0    0      0     0
ReadRemoteRpc             0      0      0      0     0      0      0     0     0      0    0      0     0
ReadRemotePhyIO           0      0      0      0     0      0      0     0     0      0    0      0     0

STATS-NAME                  VALUE
BusyWaits                       0
LRUNumLocks                136253
LRUNumSpinsWoTO                 0      0%
LRUNumSpinLoops              2780
LRUNumTimeOuts               2780  -0.02%
BmapHTNumLocks                  0
BmapHTNumWaits                  0      0%
CacheTeamTimesWoken             1
CacheTeamNumAsleep             10
BmapHTMaxEntries             4096
BmapHTNEntries                 17
BmapHTNInserts               2334
BmapHTNCollisn                  0
BmapHTNFinds                  183
BmapHTNHits                     0
BmapHTNHits1                    0
BmapHTNHits2                    0
BmapHTNClears                2327
BmapHTNLChain                   0
BmapHTNRehash                   0
BlockmapMutexsNLocks            0
BlockmapMutexsNWaits            0
BlockmapUID                  2380
BlockmapUIDnallocs           2335
BlockmapRegEver              2344
BlockmapRegisters            2334
BufHTNBuckets                4608
BufHTNEntries                  24
BufHTNw2orMore                  0
BufHTMaxBucketSize              3
BufHTNFoiledOps                 0
IONumLocks                      0
IONumWaits                      0      0%

```



<a name="loioa48026b384f2101598ebdc87a2fbefd9__section_xj3_nkf_nbb"/>

## Example 3

The following example displays output for the Buffer Pool \(Main and Temporary\) after 20 minutes:

```
sp_iqsysmon '00:20:00', 'mbufpool tbufpool';
```

```
==============================
Buffer Pool (Main)
==============================
 
STATS-NAME            TOTAL NONE TXTPOS TXTDOC CMPACT BTREEV BTREEF BV   VDO DBEXT DBID  SORT STORE GARRAY
MovedToMRU            68731    0      0      0      0   9094   2767  0 21083     0    0     0     0    303
MovedToWash               0    0      0      0      0      0      0  0     0     0    0     0     0      0
RemovedFromLRU        67564    0      0      0      0   9020   2597  0 20830     0    0     0     0    274
RemovedFromWash       11457    0      0      0      0   1559    356  0  2189     0    0     0     0     68
RemovedInScanMode         0    0      0      0      0      0      0  0     0     0    0     0     0      0
MovedToPSList             0    0      0      0      0      0      0  0     0     0    0     0     0      0
RemovedFromPSList         0    0      0      0      0      0      0  0     0     0    0     0     0      0

STATS-NAME (cont'd)  BARRAY BLKMAP   HASH   CKPT    BM   TEST   CMID RIDCA   LOB LVCRID FILE RIDMAP RVLOG
MovedToMRU             2169   8561      0      0 24754      0      0      0    0      0    0      0     0
MovedToWash               0      0      0      0     0      0      0      0    0      0    0      0     0
RemovedFromLRU         2065   8330      0      0 24448      0      0      0    0      0    0      0     0
RemovedFromWash         233   1437      0      0  5615      0      0      0    0      0    0      0     0
RemovedInScanMode         0      0      0      0     0      0      0      0    0      0    0      0     0
MovedToPSList             0      0      0      0     0      0      0      0    0      0    0      0     0
RemovedFromPSList         0      0      0      0     0      0      0      0    0      0    0      0     0

STATS-NAME                  VALUE
Pages                        2787
InUse                        1208 ( 43.3% )
Dirty                          11 ( 0.4% )
Pinned                         19 ( 0.7% )
Flushes                         0
FlushedBufferCount              0
GetPageFrame                 1605
GetPageFrameFailure             0
GotEmptyFrame                1605
Washed                          0
TimesSweepersWoken              0
PriorityWashed                  0
NPrioritySweepersWoken          0
washTeamSize                   10
WashMaxSize                   455 ( 16.3% )
washNBuffers                  455 ( 16.3% )
washNDirtyBuffers               0 ( 0.0% )
washSignalThreshold            46 ( 1.7% )
washNActiveSweepers             0
NPriorityWashBuffers            0
NActivePrioritySweepers         0
washIntensity                   0
FlushAndEmpties                 0
EmptiedBufferCount              0
EmptiedSkippedCount             0
EmptiedWriteCount               0
EmptiedErrorCount               0
nAffinityTotal                  0 ( 0.0% )
nAffinityArea                   0 ( 0.0% )

==============================
Buffer Pool (Temporary)
==============================
 
STATS-NAME            TOTAL NONE TXTPOS TXTDOC CMPACT BTREEV BTREEF BV VDO DBEXT DBID  SORT STORE GARRAY
MovedToMRU            30514    0      0      0      0      0      0  0   0     0    0  1218   696      0
MovedToWash             258    0      0      0      0      0      0  0   0     0    0     0   256      0
RemovedFromLRU        30506    0      0      0      0      0      0  0   0     0    0  1218   694      0
RemovedFromWash       30503    0      0      0      0      0      0  0   0     0    0  1218   694      0
RemovedInScanMode         0    0      0      0      0      0      0  0   0     0    0     0     0      0
MovedToPSList             0    0      0      0      0      0      0  0   0     0    0     0     0      0
RemovedFromPSList         0    0      0      0      0      0      0  0   0     0    0     0     0      0

STATS-NAME (cont'd)  BARRAY BLKMAP   HASH   CKPT    BM   TEST   CMID RIDCA   LOB LVCRID FILE RIDMAP RVLOG
MovedToMRU                0   8575    124      0 19898      0      0     0     0      0    3      0     0
MovedToWash               0      0      0      0     0      0      0     0     0      0    2      0     0
RemovedFromLRU            0   8569    124      0 19898      0      0     0     0      0    3      0     0
RemovedFromWash           0   8569    124      0 19898      0      0     0     0      0    0      0     0
RemovedInScanMode         0      0      0      0     0      0      0     0     0      0    0      0     0
MovedToPSList             0      0      0      0     0      0      0     0     0      0    0      0     0
RemovedFromPSList         0      0      0      0     0      0      0     0     0      0    0      0     0

STATS-NAME                 VALUE
Pages                        2787
InUse                          24 ( 0.9% )
Dirty                          17 ( 0.6% )
Pinned                          4 ( 0.1% )
Flushes                         0
FlushedBufferCount              0
GetPageFrame                 5684
GetPageFrameFailure             0
GotEmptyFrame                5684
Washed                          0
TimesSweepersWoken              0
PriorityWashed                  0
NPrioritySweepersWoken          0
washTeamSize                   10
WashMaxSize                   455 ( 16.3% )
washNBuffers                   20 ( 0.7% )
washNDirtyBuffers              13 ( 0.5% )
washSignalThreshold            46 ( 1.7% )
washNActiveSweepers             0
NPriorityWashBuffers            0
NActivePrioritySweepers         0
washIntensity                   0
FlushAndEmpties                 0
EmptiedBufferCount              0
EmptiedSkippedCount             0
EmptiedWriteCount               0
EmptiedErrorCount               0
nAffinityTotal                  0 ( 0.0% )
nAffinityArea                   0 ( 0.0% )

```



<a name="loioa48026b384f2101598ebdc87a2fbefd9__section_qp5_qkf_nbb"/>

## Example 4

The following example displays output for the Prefetch Manager \(Main and Temporary\) after 20 minutes:

```
sp_iqsysmon '00:20:00', 'mprefetch tprefetch';
```

```
==============================
Prefetch Manager (Main)
==============================

STATS-NAME                  VALUE
PFMgrNThreads                  10
PFMgrNSubmitted                81
PFMgrNDropped                   0
PFMgrNValid                     0
PFMgrNRead                      1
PFMgrNReading                   0
PFMgrCondVar                Locks  0  Lock-Waits 0 ( 0.0% )  Signals 0  Broadcasts  2  Waits  2

==============================
Prefetch Manager (Temporary)
==============================

STATS-NAME                  VALUE
PFMgrNThreads                  10
PFMgrNSubmitted                 1
PFMgrNDropped                   0
PFMgrNValid                     0
PFMgrNRead                      1
PFMgrNReading                   0
PFMgrCondVar                Locks  0  Lock-Waits 0 ( 0.0% )  Signals 0  Broadcasts  2  Waits  2
```



<a name="loioa48026b384f2101598ebdc87a2fbefd9__section_tdk_skf_nbb"/>

## Example 5

The following example displays output for the data lake Relational Engine Store Free List \(Main and Temporary\) after 20 minutes:

```
sp_iqsysmon '00:20:00', 'mfreelist tfreelist';
```

```
==============================
IQ Store (Main) Free List
==============================

STATS-NAME                  VALUE
FLBitCount                  74036
FLIsOutOfSpace                NO
FLMutexLocks                    0
FLMutexWaits                    0 ( 0.0% )

==============================
IQ Store (Temporary) Free List
==============================

STATS-NAME                  VALUE
FLBitCount                   4784
FLIsOutOfSpace                NO
FLMutexLocks                    0
FLMutexWaits                    0 ( 0.0% )
```



<a name="loioa48026b384f2101598ebdc87a2fbefd9__section_l14_tkf_nbb"/>

## Example 6

The following example displays output for Memory Manager, Thread Manager, CPU utilization, Transaction Manager after 20 minutes:

```
sp_iqsysmon '00:20:00', 'memory threads cpu txn';
```

```
==============================
Memory Manager
==============================

STATS-NAME                      VALUE
MemAllocated                 67599536  ( 66015 KB )
MemAllocatedMax             160044816 ( 156293 KB )
MemAllocatedEver           1009672456 ( 986008 KB )
MemNAllocated                   77309
MemNAllocatedEver              914028
MemNTimesLocked                     0
MemNTimesWaited                     0      ( 0.0 %)

==============================
Thread Manager
==============================
 
STATS-NAME                      VALUE
ThrNumOfCpus                        4
ThreadLimit                        99
ThrNumThreads                      98     ( 99.0 %)
ThrReserved                        15     ( 15.2 %)
ThrNumFree                         55     ( 55.6 %)
NumThrUsed                         44     ( 44.4 %)
UsedPerActiveCmd                   22
ThrNTeamsInUse                      5
ThrMaxTeams                         7
NumTeamsAlloc                     238
TeamThrAlloc                      421
SingleThrAlloc                    492
ThrMutexLocks                       0
ThrMutexWaits                       0      ( 0.0 %)

==============================
CPU time statistics
==============================

STATS-NAME                      VALUE
Elapsed Seconds                 59.65     ( 25.0 %)
CPU User Seconds                37.79     ( 15.8 %)
CPU Sys Seconds                  1.89      ( 0.8 %)
CPU Total Seconds               39.68     ( 16.6 %)

==============================
Transaction Manager
==============================

STATS-NAME                      VALUE
TxnMgrNPending                      0
TxnMgrNBlocked                      2
TxnMgrNWaiting                      0
TxnMgrPCcondvar                 Locks     0       Lock-Wait 0 ( 0.0 %)  Signals 0  Broadcasts 2 Waits 2
TxnMgrTxnIDseq                    407
TxnMgrtxncblock                 Locks     0       Lock-Wait 0 ( 0.0 %)
TxnMgrVersionID                     0
TxnMgrOAVI                          0
TxnMgrVersionLock               Locks     0       Lock-Wait 0 ( 0.0 %)  Signals 0  Broadcasts 0 Waits 0

```



<a name="loioa48026b384f2101598ebdc87a2fbefd9__section_wj5_5kf_nbb"/>

## Example 7

The following example displays output for server context and catalog statistics after 20 minutes:

```
sp_iqsysmon '00:20:00', 'context catalog';
```

```
==============================
Context Server statistics
==============================

STATS-NAME                  VALUE
StCntxNumConns                  1
StCntxNResource                16
StCntxNOrigResource            18
StCntxNWaiting                  0
StCntxNWaited                   0
StCntxNAdmitted              1116
StCntxLock                  Locks  0 Lock-Waits  0 ( 0.0 %)
StCntxCondVar               Locks  0 Lock-Waits  0 ( 0.0 %)

==============================
Catalog, DB Log, and Repository statistics
==============================

STATS-NAME                  VALUE 
CatalogLock               RdLocks  0    RdWaits  0 ( 0.0 %)  RdTryFails 0  WrLocks  30037  WrWaits  0 ( 0.0 %)  WrTryFail 0
DbLogMLock                  Locks  0 Lock-Waits  0 ( 0.0 %)
DbLogSLock                  Locks  0 Lock-Waits  0 ( 0.0 %)
RepositoryNList                 0
RepositoryLock              Locks  1  SpinsWoTO  0 ( 0.0 %)      Spins  0  TimeOuts     0 ( 0.0 %)

```

