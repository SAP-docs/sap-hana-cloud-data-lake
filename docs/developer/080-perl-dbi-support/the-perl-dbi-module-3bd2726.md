<!-- loio3bd2726b6c5f1014be4184272f49fe7f -->

# The Perl DBI Module

To use the DBD::SQLAnywhere interface from a Perl script, you must first tell Perl that you plan to use the Perl DBI module. To do so, include the following line at the top of the file.

```
use DBI;
```

In addition, it is highly recommended that you run Perl in strict mode. This statement, which makes explicit variable definitions mandatory, is likely to greatly reduce the chance that you will run into mysterious errors due to such common mistakes as typographical errors.

```
#!/usr/local/bin/perl -w
#
use DBI;
use strict;
```

The Perl DBI module automatically loads the DBD drivers, including DBD::SQLAnywhere, as required.

