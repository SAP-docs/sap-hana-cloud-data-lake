<!-- loioa62b0c8b84f210159120ac171331719c -->

# Data Extraction Options

The data extraction facility allows you to extract data from a database by redirecting the output of a `SELECT` statement from the standard interface to one or more disk files or named pipes.

The `TEMP_EXTRACT_...` database options are used to control the data extraction feature.

**Related Information**  


[TEMP\_EXTRACT\_ACCESS\_KEY\_ID Option \(Deprecated\) for Data Lake Relational Engine](temp-extract-access-key-id-option-deprecated-for-data-lake-relational-engine-924c9f8.md "Supplies the AWS access key. You must specify the access key when extracting data from data lake Relational Engine to an Amazon S3 bucket.")

[TEMP\_EXTRACT\_APPEND Option for Data Lake Relational Engine](temp-extract-append-option-for-data-lake-relational-engine-a65b43e.md "Specifies that any rows extracted by the data extraction facility are added to the end of an output file.")

[TEMP\_EXTRACT\_AZURE\_BLOCK\_SIZE\_MB Option \(Deprecated\) for Data Lake Relational Engine](temp-extract-azure-block-size-mb-option-deprecated-for-data-lake-relational-engine-36c211c.md "Specifies the size of blocks in an Azure block blob, in MB.")

[TEMP\_EXTRACT\_BINARY Option for Data Lake Relational Engine](temp-extract-binary-option-for-data-lake-relational-engine-a65bc23.md "In combination with the TEMP_EXTRACT_SWAP option, specifies the type of extraction performed by the data extraction facility.")

[TEMP\_EXTRACT\_COLUMN\_DELIMITER Option for Data Lake Relational Engine](temp-extract-column-delimiter-option-for-data-lake-relational-engine-a65c4d6.md "Specifies the delimiter between columns in the output of the data extraction facility for an ASCII extraction.")

[TEMP\_EXTRACT\_CONNECTION\_STRING Option \(Deprecated\) for Data Lake Relational Engine](temp-extract-connection-string-option-deprecated-for-data-lake-relational-engine-b96926b.md "Specifies the connection string of your Azure storage account.")

[TEMP\_EXTRACT\_COMPRESS Option for Data Lake Relational Engine](temp-extract-compress-option-for-data-lake-relational-engine-aef24bc.md "Writes the output file for exports in gzip format. This results in a significant savings of storagespace when exporting tables.")

[TEMP\_EXTRACT\_DIRECTORY Option for Data Lake Relational Engine](temp-extract-directory-option-for-data-lake-relational-engine-a65cd33.md "Controls whether a user is allowed to use the data extraction facility. Also controls the directory into which temp extract files are placed, and overrides a directory path specified in the TEMP_EXTRACT_NAMEN option.")

[TEMP\_EXTRACT\_ESCAPE\_QUOTES Option for Data Lake Relational Engine](temp-extract-escape-quotes-option-for-data-lake-relational-engine-a65d50c.md "Specifies whether all quotes in fields containing quotes are escaped in the output of the data extraction facility for an ASCII extraction.")

[TEMP\_EXTRACT\_FILE\_EXTENSION Option for Data Lake Relational Engine](temp-extract-file-extension-option-for-data-lake-relational-engine-896be73.md "Sets the file name extension for the generated output file of the data parallel extraction facility. When you specify the TEMP_EXTRACT_FILE_EXTENSION option, each file name generated becomes prefix thread_ID_filecount.file extension.")

[TEMP\_EXTRACT\_FILE\_PREFIX Option for Data Lake Relational Engine](temp-extract-file-prefix-option-for-data-lake-relational-engine-09cd773.md "Sets the prefix of file name for the generated output file of the data parallel extraction facility. thread_ID starts from 1. filecount starts from 1 for each thread ID. Thefilecount part increments when the size of the output file reaches the file size limit specified by the TEMP_EXTRACT_SIZE option.")

[TEMP\_EXTRACT\_GZ\_COMPRESSION\_LEVEL Option for Data Lake Relational Engine](temp-extract-gz-compression-level-option-for-data-lake-relational-engine-ee9f6aa.md "The compression level balances compression with speed when the TEMP_EXTRACT_COMPRESS option is set to ON.")

[TEMP\_EXTRACT\_LENGTH\_PREFIX Option for Data Lake Relational Engine](temp-extract-length-prefix-option-for-data-lake-relational-engine-1126138.md "Adds a prefix field of specified length (byte) for a varchar or varbinary column in the generated output file. This PREFIX field in the extract file holds the length of the column data.")

[TEMP\_EXTRACT\_MAX\_PARALLEL\_DEGREE Option for Data Lake Relational Engine](temp-extract-max-parallel-degree-option-for-data-lake-relational-engine-00f65e6.md "Sets the maximum parallel degree for the data extraction facility. The TEMP_EXTRACT_MAX_PARALLEL_DEGREE option limits the maximum number of threads that run in parallel to extract data.")

[TEMP\_EXTRACT\_NAME<N\> Option for Data Lake Relational Engine](temp-extract-name-n-option-for-data-lake-relational-engine-a65dd19.md "Specifies the data lake Filescontainer object file name, or theAzure block blob name, or the Amazon S3 bucket object name you’re extracting to. You must specify the name when extracting data from data lake Relational Engine to cloud storage.")

[TEMP\_EXTRACT\_NULL\_AS\_EMPTY Option for Data Lake Relational Engine](temp-extract-null-as-empty-option-for-data-lake-relational-engine-a65e506.md "Controls the representation of null values in the output of the data extraction facility for an ASCII extraction.")

[TEMP\_EXTRACT\_NULL\_AS\_ZERO Option for Data Lake Relational Engine](temp-extract-null-as-zero-option-for-data-lake-relational-engine-a65ed25.md "Controls the representation of null values in the output of the data extraction facility for an ASCII extraction.")

[TEMP\_EXTRACT\_QUOTE Option for Data Lake Relational Engine](temp-extract-quote-option-for-data-lake-relational-engine-a65f5a3.md "Specifies the string to be used as the quote to enclose fields in the output of the data extraction facility for an ASCII extraction, when either the TEMP_EXTRACT_QUOTES option or the TEMP_EXTRACT_QUOTES_ALL option is set ON.")

[TEMP\_EXTRACT\_QUOTES Option for Data Lake Relational Engine](temp-extract-quotes-option-for-data-lake-relational-engine-a65fdb5.md "Specifies that string fields are enclosed in quotes in the output of the data extraction facility for an ASCII extraction.")

[TEMP\_EXTRACT\_QUOTES\_ALL Option for Data Lake Relational Engine](temp-extract-quotes-all-option-for-data-lake-relational-engine-a6605bd.md "Specifies that all fields are enclosed in quotes in the output of the data extraction facility for an ASCII extraction.")

[TEMP\_EXTRACT\_REGION Option \(Deprecated\) for Data Lake Relational Engine](temp-extract-region-option-deprecated-for-data-lake-relational-engine-5a09183.md "Specifies the AWS region where your Amazon S3 bucket resides. You must specify the region when extracting data from the Amazon S3 bucket.")

[TEMP\_EXTRACT\_ROW\_DELIMITER Option for Data Lake Relational Engine](temp-extract-row-delimiter-option-for-data-lake-relational-engine-a660d8f.md "Specifies the delimiter between rows in the output of the data extraction facility for an ASCII extraction.")

[TEMP\_EXTRACT\_SECRET\_ACCESS\_KEY Option \(Deprecated\) for Data Lake Relational Engine](temp-extract-secret-access-key-option-deprecated-for-data-lake-relational-engine-0db4937.md "Supplies the AWS secret access key. You must specify the secret access key when extracting data from data lake Relational Engine to an Amazon S3 bucket.")

[TEMP\_EXTRACT\_SIZE Option for Data Lake Relational Engine](temp-extract-size-option-for-data-lake-relational-engine-096c15c.md "Sets the maximum size (KB) of the corresponding output files generated by the parallel data extraction facility.")

[TEMP\_EXTRACT\_SIZE<N\> Options for Data Lake Relational Engine](temp-extract-size-n-options-for-data-lake-relational-engine-a6615dd.md "Specifies the maximum sizes of the corresponding output files used by the data extraction facility.")

[TEMP\_EXTRACT\_SWAP Option for Data Lake Relational Engine](temp-extract-swap-option-for-data-lake-relational-engine-a661dc2.md "In combination with the TEMP_EXTRACT_BINARY option, specifies the type of extraction performed by the data extraction facility.")

[TEMP\_EXTRACT\_VARYING Option for Data Lake Relational Engine](temp-extract-varying-option-for-data-lake-relational-engine-ceb244e.md "Used in conjunction with TEMP_EXTRACT_LENGTH_PREFIX, the TEMP_EXTRACT_VARYING option outputs varchar or varbinary column data in a variable-length format in the extracted file. The prefix field specified by TEMP_EXTRACT_LENGTH_PREFIX option holds the length of column data.")

