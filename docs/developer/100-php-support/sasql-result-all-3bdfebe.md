<!-- loio3bdfebe86c5f10149a93f32be807efce -->

# sasql\_result\_all

Fetches all results and generates an HTML output table with an optional formatting string.



```
bool sasql_result_all( resource <$result> 
[, <$html_table_format_string> 
[, <$html_table_header_format_string> 
[, <$html_table_row_format_string> 
[, <$html_table_cell_format_string> 
] ] ] ] )
```



## Parameters

$result
:   The result resource returned by the sasql\_query function.

$html\_table\_format\_string
:   A format string that applies to HTML tables. For example, ***"Border=1; Cellpadding=5"***. The special value none does not create an HTML table. This is useful to customize your column names or scripts. To avoid specifying an explicit value for this parameter, use NULL for the parameter value.

$html\_table\_header\_format\_string
:   A format string that applies to column headings for HTML tables. For example, ***"bgcolor=\#FF9533"***. The special value none does not create an HTML table. This is useful to customize your column names or scripts. To avoid specifying an explicit value for this parameter, use NULL for the parameter value.

$html\_table\_row\_format\_string
:   A format string that applies to rows within HTML tables. For example, ***"onclick='alert\('this'\)'"***. If you would like different formats that alternate, use the special token \><. The left side of the token indicates which format to use on odd rows and the right side of the token is used to format even rows. If you do not place this token in your format string, all rows have the same format. If you do not want to specify an explicit value for this parameter, use NULL for the parameter value.

$html\_table\_cell\_format\_string
:   A format string that applies to cells within HTML table rows. For example, ***"onclick='alert\('this'\)'"***. If you do not want to specify an explicit value for this parameter, use NULL for the parameter value.



## Returns

TRUE on success or FALSE on failure.



## Remarks

Fetches all results of the *<$result\>* and generates an HTML output table with an optional formatting string.

