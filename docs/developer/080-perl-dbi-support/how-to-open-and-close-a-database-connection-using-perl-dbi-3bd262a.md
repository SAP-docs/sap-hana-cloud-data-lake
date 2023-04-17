<!-- loio3bd262ab6c5f10149891c5710c39a0a2 -->

# How to Open and Close a Database Connection Using Perl DBI

Generally, you open a single connection to a database and then perform all the required operations through it by executing a sequence of SQL statements.

To open a connection, you use the *connect* method. The return value is a handle to the database connection that you use to perform subsequent operations on that connection.

The parameters to the connect method are as follows:

1.  "DBI:SQLAnywhere:" and additional connection parameters separated by semicolons.

2.  A user name. Unless this string is blank, ";UID=*<value\>*" is appended to the connection string.

3.  A password value. Unless this string is blank, ";PWD=*<value\>*" is appended to the connection string.

4.  A pointer to a hash of default values. Settings such as AutoCommit, RaiseError, and PrintError may be set in this manner.


The following code sample opens and closes a connection to the sample database. You must start the database server and sample database before running this script.

```
#!/usr/local/bin/perl -w
#
use DBI;
use strict;
my $database = "iqdemo";
my $data_src = "DBI:SQLAnywhere:SERVER=$database;DBN=$database";
my $uid      = "HDLADMIN";
my $pwd      = "<password>";
my %defaults = (
     AutoCommit => 1, # Autocommit enabled.
     PrintError => 0  # Errors not automatically printed.
   );
my $dbh = DBI->connect($data_src, $uid, $pwd, \%defaults)
  or die "Cannot connect to $data_src: $DBI::errstr\n";
$dbh->disconnect;
exit(0);
__END__
```

Optionally, you can append the user name or password value to the data-source string instead of supplying them as separate parameters. If you do so, supply a blank string for the corresponding argument. For example, in the above script may be altered by replacing the statement that opens the connections with these statements:

```
$data_src .= ";UID=$uid";
$data_src .= ";PWD=$<password>";
my $dbh = DBI->connect($data_src, '', '', \%defaults)
  or die "Cannot connect to $data_src: $DBI::errstr\n";
```

