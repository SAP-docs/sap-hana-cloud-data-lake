<!-- loio5720d63b095340469e09c2f3ea621e57 -->

# Permission Checking Order

Schema-level permission checking is performed when access to the specific operation is not allowed by existing system and object-level permissions.



If no granted system privilege allows the operation, then permission is checked at the object level. If the operation is still not allowed by the granted object-level privileges, then permission is checked at the schema level object. With the exception of backup and restore table, which requires additional system privileges, if you own the schema, then you can perform all operations on that schema.

For example:

1.  If a user has the SELECT ANY TABLE system privilege, then they can SELECT from any table in any schema.
2.  If a user has the SELECT object-level privilege on test\_schema.table1, but not SELECT on the schema test\_schema, then they can still SELECT from table1.
3.  If a user has EXECUTE on the schema, then they can execute any procedures or functions in the schema.

