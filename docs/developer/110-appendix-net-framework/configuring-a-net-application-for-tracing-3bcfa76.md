<!-- loio3bcfa7656c5f10149b09807ebfeefa70 -->

# Configuring a .NET Application for Tracing

Enable tracing on the TableViewer sample application by creating a configuration file that references the ConsoleTraceListener and TextWriterTraceListener listeners, removes the default listener, and enables all switches that would otherwise be set to 0.



## Prerequisites

You must have Microsoft Visual Studio installed.



## Procedure

1.  Open the TableViewer sample in Microsoft Visual Studio.

    Start Microsoft Visual Studio and open the <code><i>%IQDIRSAMP17%</i>\SQLAnywhere\ADO.NET\TableViewer\TableViewer.sln</code>.

2.  Create an application file named `App.config`.

    Choose *Add* \> *New Item* and selecting *Application Configuration File*. Place the following configuration information in this file:

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

3.  Rebuild the application.

4.  Click *Debug* \> *Start Debugging*.




## Results

When the application finishes execution, the trace output is recorded in the `bin\Debug\myTrace.log` file.



## Next Steps

View the trace log in the *Output* window of Microsoft Visual Studio.

