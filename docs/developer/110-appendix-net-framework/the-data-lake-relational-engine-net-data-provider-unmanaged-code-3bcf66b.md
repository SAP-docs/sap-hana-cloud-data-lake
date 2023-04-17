<!-- loio3bcf66b76c5f1014b219867750fa0899 -->

# The Data Lake Relational Engine .NET Data Provider Unmanaged Code

When the .NET Data Provider is first loaded by a .NET application \(usually when making a database connection using SAConnection\), it unpacks a DLL that contains the provider's unmanaged code.

The file <code>dbdata<i>17</i>.dll</code> is placed by the provider in a subdirectory of the directory identified using the following strategy.

1.  The first directory it attempts to use for unloading is the one returned by the first of the following:

    -   The path identified by the *TMP* environment variable.
    -   The path identified by the *TEMP* environment variable.
    -   The path identified by the *USERPROFILE* environment variable.

2.  If the identified directory is inaccessible, then the provider will attempt to use the current working directory.

3.  If the current working directory is inaccessible, then the provider will attempt to use the directory from where the application itself was loaded.


The subdirectory name will take the form of a GUID with a suffix including the version number, a machine architecture tag when not 32-bit \(for example, .x64\), and an index number used to guarantee uniqueness. The following is an example of a possible subdirectory name for 32-bit architecture.

```
{16AA8FB8-4A98-4757-B7A5-0FF22C0A6E33}_1700_1
```

The following is an example of a possible subdirectory name for 64-bit architecture.

```
{16AA8FB8-4A98-4757-B7A5-0FF22C0A6E33}_1700.x64_1
```

