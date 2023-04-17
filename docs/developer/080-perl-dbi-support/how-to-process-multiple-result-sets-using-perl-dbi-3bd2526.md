<!-- loio3bd2526c6c5f1014a76fbd7da42b3b87 -->

# How to Process Multiple Result Sets Using Perl DBI

The method for handling multiple result sets from a query involves wrapping the fetch loop within another loop that moves between result sets.

SQL statements that return multiple result sets must be prepared before being executed. The *prepare* method returns a handle to the statement. You use the handle to execute the statement, then retrieve meta information about the result set and the rows of each of the result sets.

```
#!/usr/local/bin/perl -w
#
use DBI;
use strict;
my $database = "iqdemo";
my $data_src = "DBI:SQLAnywhere:SERVER=$database;DBN=$database";
my $uid      = "HDLADMIN";
my $pwd      = "<password>";
my $sel_stmt = "SELECT ID, GivenName, Surname
                  FROM Customers
                  ORDER BY GivenName, Surname;
                SELECT * 
                  FROM Departments 
                  ORDER BY DepartmentID"; 
my %defaults = (
     AutoCommit => 0, # Require explicit commit or rollback.
     PrintError => 0
   );
my $dbh = DBI->connect($data_src, $uid, $pwd, \%defaults)
  or die "Cannot connect to $data_src: $DBI::errstr\n";
&db_query($sel_stmt, $dbh);
$dbh->rollback;
$dbh->disconnect;
exit(0);

sub db_query {
      my($sel, $dbh) = @_;
      my($row, $sth) = undef;
      $sth = $dbh->prepare($sel);
      $sth->execute;
      do {
          print "Fields:     $sth->{NUM_OF_FIELDS}\n";
          print "Params:     $sth->{NUM_OF_PARAMS}\n\n";
          print join("\t\t", @{$sth->{NAME}}), "\n\n";
          while($row = $sth->fetchrow_arrayref) {
             print join("\t\t", @$row), "\n";
          }
          print "---end of results---\n\n";
      } while (defined $sth->more_results);
      $sth = undef;
}
__END__
```

