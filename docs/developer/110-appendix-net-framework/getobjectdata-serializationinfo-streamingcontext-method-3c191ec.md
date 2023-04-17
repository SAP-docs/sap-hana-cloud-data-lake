<!-- loio3c191ec06c5f10148bd8e09686af6940 -->

# GetObjectData\(SerializationInfo, StreamingContext\) Method

Sets the SerializationInfo with information about the exception.



Visual Basic
:   ```
Public Overrides Sub GetObjectData (
    ByVal info As SerializationInfo,
    ByVal context As StreamingContext
)
```

C\#
:   ```
public override void GetObjectData (
    SerializationInfo info,
    StreamingContext context
)
```



## Parameters

info
:   The SerializationInfo that holds the serialized object data about the exception being thrown.

context
:   The StreamingContext that contains contextual information about the source or destination.



## Remarks

Overrides Exception.GetObjectData.

