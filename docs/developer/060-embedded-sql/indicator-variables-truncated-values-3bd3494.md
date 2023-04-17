<!-- loio3bd349416c5f10148a76c0f06f63924d -->

# Indicator Variables: Truncated Values

Indicator variables indicate whether any fetched values were truncated to fit into a host variable. This enables applications to handle truncation appropriately.

If a value is truncated on fetching, the indicator variable is set to a positive value, containing the actual length of the database value before truncation. If the actual length of the database value is greater than 32767 bytes, then the indicator variable contains 32767.

