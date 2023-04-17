<!-- loio3bcfaf8a6c5f1014b338e17083213281 -->

# .NET Tracing Support

The .NET Data Provider supports tracing using the .NET tracing feature.

By default, tracing is disabled. To enable tracing, specify the trace source in your application's configuration file. The following is an example of a configuration file:

```
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
<system.diagnostics>
<sources>
 <source name="Sap.Data.SQLAnywhere" 
         switchName="SASourceSwitch" 
         switchType="System.Diagnostics.SourceSwitch">
  <listeners>
   <add name="ConsoleListener" 
        type="System.Diagnostics.ConsoleTraceListener"/>
   <add name="EventListener" 
        type="System.Diagnostics.EventLogTraceListener" 
        initializeData="MyEventLog"/>
   <add name="TraceLogListener" 
        type="System.Diagnostics.TextWriterTraceListener" 
        initializeData="myTrace.log" 
        traceOutputOptions="ProcessId, ThreadId, Timestamp"/>
   <remove name="Default"/>
  </listeners>
 </source>
</sources>
<switches>
 <add name="SASourceSwitch" value="All"/>
 <add name="SATraceAllSwitch" value="1" />
 <add name="SATraceExceptionSwitch" value="1" />
 <add name="SATraceFunctionSwitch" value="1" />
 <add name="SATracePoolingSwitch" value="1" />
 <add name="SATracePropertySwitch" value="1" />
</switches>
</system.diagnostics>
</configuration>
```

There are four types of trace listeners referenced in the configuration file shown above.

ConsoleTraceListener
:   Tracing or debugging output is directed to either the standard output or the standard error stream. When using Microsoft Visual Studio, output appears in the *Output* window.

DefaultTraceListener
:   This listener is automatically added to the Debug.Listeners and Trace.Listeners collections using the name "Default". Tracing or debugging output is directed to either the standard output or the standard error stream. When using Microsoft Visual Studio, output appears in the *Output* window. To avoid duplication of output produced by the ConsoleTraceListener, this listener is removed.

EventLogTraceListener
:   Tracing or debugging output is directed to an EventLog identified in the *initializeData* option. In the example, the event log is named MyEventLog. Writing to the system event log requires administrator privileges and is not a recommended method for debugging applications.

TextWriterTraceListener
:   Tracing or debugging output is directed to a TextWriter which writes the stream to the file identified in the *initializeData* option.

To disable tracing to any of the trace listeners described above, remove the corresponding *add* entry under *<listeners\>*.

The trace configuration information is placed in the application's project folder in the `App.config` file. If the file does not exist, it can be created and added to the project using Microsoft Visual Studio by choosing *Add* \> *New Item* and selecting *Application Configuration File*.

The traceOutputOptions can be specified for any listener and include the following:

Callstack
:   Write the call stack, which is represented by the return value of the Environment.StackTrace property.

DateTime
:   Write the date and time.

LogicalOperationStack
:   Write the logical operation stack, which is represented by the return value of the CorrelationManager.LogicalOperationStack property.

None
:   Do not write any elements.

ProcessId
:   Write the process identity, which is represented by the return value of the Process.Id property.

ThreadId
:   Write the thread identity, which is represented by the return value of the Thread.ManagedThreadId property for the current thread.

Timestamp
:   Write the timestamp, which is represented by the return value of the System.Diagnostics.Stopwatch.GetTimeStamp method.

The example configuration file, shown earlier, specifies trace output options for the TextWriterTraceListener only.

You can limit what is traced by setting specific trace options. By default the numeric-valued trace option settings are all 0. The trace options that can be set include the following:

SASourceSwitch
:   SASourceSwitch can take any of the following values. If it is Off then there is no tracing.

    Off
    :   Does not allow any events through.

    Critical
    :   Allows only Critical events through.

    Error
    :   Allows Critical and Error events through.

    Warning
    :   Allows Critical, Error, and Warning events through.

    Information
    :   Allows Critical, Error, Warning, and Information events through.

    Verbose
    :   Allows Critical, Error, Warning, Information, and Verbose events through.

    ActivityTracing
    :   Allows the Stop, Start, Suspend, Transfer, and Resume events through.

    All
    :   Allows all events through.

    Here is an example setting.

    ```
    <add name="SASourceSwitch" value="Error"/>
    ```

SATraceAllSwitch
:   All the trace options are enabled. You do not need to set any other options since they are all selected. You cannot disable individual options if you choose this option. For example, the following will not disable exception tracing.

    ```
    <add name="SATraceAllSwitch" value="1" />
    <add name="SATraceExceptionSwitch" value="0" />
    ```

SATraceExceptionSwitch
:   All exceptions are logged. Trace messages have the following form.

    ```
    <Type|ERR> message='message_text'[ nativeError=error_number]
    ```

    The nativeError=error\_number text will only be displayed if there is an SAException object.

SATraceFunctionSwitch
:   All method scope entry/exits are logged. Trace messages have any of the following forms.

    ```
    enter_nnn <sa.class_name.method_name|API> [object_id#][parameter_names]
    leave_nnn
    ```

    The nnn is an integer representing the scope nesting level 1, 2, 3, ... The optional parameter\_names is a list of parameter names separated by spaces.

SATracePoolingSwitch
:   All connection pooling is logged. Trace messages have any of the following forms.

    ```
    <sa.ConnectionPool.AllocateConnection|CPOOL> connectionString='connection_text'
    <sa.ConnectionPool.RemoveConnection|CPOOL> connectionString='connection_text'
    <sa.ConnectionPool.ReturnConnection|CPOOL> connectionString='connection_text'
    <sa.ConnectionPool.ReuseConnection|CPOOL> connectionString='connection_text'
    ```

SATracePropertySwitch
:   All property setting and retrieval is logged. Trace messages have any of the following forms.

    ```
    <sa.class_name.get_property_name|API> object_id#
    <sa.class_name.set_property_name|API> object_id#
    ```

