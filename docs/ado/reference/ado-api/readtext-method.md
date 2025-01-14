---
title: "ReadText Method"
description: "ReadText Method"
author: rothja
ms.author: jroth
ms.date: "01/19/2017"
ms.prod: sql
ms.technology: ado
ms.topic: reference
f1_keywords:
  - "_Stream::raw_ReadText"
  - "_Stream::ReadText"
helpviewer_keywords:
  - "ReadText method [ADO]"
apitype: "COM"
---
# ReadText Method
Reads specified number of characters from a text [Stream](./stream-object-ado.md) object.  
  
## Syntax  
  
```  
  
String = Stream.ReadText ( NumChars)  
```  
  
#### Parameters  
 *NumChars*  
 Optional. A **Long** value that specifies the number of characters to read from the file, or a [StreamReadEnum](./streamreadenum.md) value. The default value is **adReadAll**.  
  
## Return Value  
 The **ReadText** method reads a specified number of characters, an entire line, or the entire stream from a **Stream** object and returns the resulting string.  
  
## Remarks  
 If *NumChar* is more than the number of characters left in the stream, only the characters remaining are returned. The string read is not padded to match the length specified by *NumChar*. If there are no characters left to read, a variant whose value is null is returned. **ReadText** cannot be used to read backwards.  
  
> [!NOTE]
>  The **ReadText** method is used with text streams ([Type](./type-property-ado-stream.md) is **adTypeText**). For binary streams (**Type** is **adTypeBinary**), use [Read](./read-method.md).  
  
 Queries that result in a large amount of XML data being returned through the **ReadText** method of the ActiveX Data Object (ADO) Stream object may take a great deal of time to execute; if this is done in a COM+ component that is invoked from an ASP page, the user's session may time out. ADO converts Stream object data from UTF-8 encoding to Unicode; the frequent memory reallocation involved in conversion of such a large quantity of data at once is quite time-consuming. To resolve, make repeated calls to the **ReadText** method of the ADO command object, and specify a smaller number of characters. Tests have shown that a value equivalent to 128K (131,072) is optimal. Response time decreases as this value is decreased. For more information, see Knowledge Base article 280067, "PRB: Retrieving very large XML Documents from SQL Server 2000 by using ReadText method of ADO stream object may be slow", in the Microsoft Knowledge Base at https://support.microsoft.com.  
  
## Applies To  
 [Stream Object (ADO)](./stream-object-ado.md)  
  
## See Also  
 [Read Method](./read-method.md)