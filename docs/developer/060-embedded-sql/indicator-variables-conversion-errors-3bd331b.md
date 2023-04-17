<!-- loio3bd331b76c5f1014a862aeefca3dace4 -->

# Indicator Variables: Conversion Errors

By default, the conversion\_error database option is set to On, and any data type conversion failure leads to an error, with no row returned.

You can use indicator variables to tell which column produced a data type conversion failure. If you set the database option conversion\_error to Off, any data type conversion failure gives a CANNOT\_CONVERT warning, rather than an error. If the column that suffered the conversion error has an indicator variable, that variable is set to a value of -2.

If you set the conversion\_error option to Off when inserting data into the database, a value of NULL is inserted when a conversion failure occurs.

