---
UID: NF:dbgeng.IDebugControl4.GetLastEventInformationWide
title: IDebugControl4::GetLastEventInformationWide method
author: windows-driver-content
description: The GetLastEventInformationWide method returns information about the last event that occurred in a target.
old-location: debugger\getlasteventinformationwide.htm
old-project: debugger
ms.assetid: 9ec4ae29-7c9f-4da6-ae5d-57de9423cb30
ms.author: windowsdriverdev
ms.date: 1/19/2018
ms.keywords: IDebugControl4::GetLastEventInformationWide, debugger.getlasteventinformationwide, GetLastEventInformationWide method [Windows Debugging], IDebugControl4 interface, GetLastEventInformationWide method [Windows Debugging], IDebugControl4 interface [Windows Debugging], GetLastEventInformationWide method, GetLastEventInformationWide, IDebugControl4, dbgeng/IDebugControl4::GetLastEventInformationWide
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: method
req.header: dbgeng.h
req.include-header: Dbgeng.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: dbgeng.h
req.dll: 
req.irql: 
topictype:
-	APIRef
-	kbSyntax
apitype:
-	COM
apilocation:
-	dbgeng.h
apiname:
-	IDebugControl4.GetLastEventInformationWide
product: Windows
targetos: Windows
req.typenames: "*PDOT4_ACTIVITY, DOT4_ACTIVITY"
---

# IDebugControl4::GetLastEventInformationWide method


## -description


The <b>GetLastEventInformationWide</b>  method returns information about the last event that occurred in a target.


## -syntax


````
HRESULT GetLastEventInformationWide(
  [out]           PULONG Type,
  [out]           PULONG ProcessId,
  [out]           PULONG ThreadId,
  [out, optional] PVOID  ExtraInformation,
  [in]            ULONG  ExtraInformationSize,
  [out, optional] PULONG ExtraInformationUsed,
  [out, optional] PWSTR  Description,
  [in]            ULONG  DescriptionSize,
  [out, optional] PULONG DescriptionUsed
);
````


## -parameters




### -param Type [out]

Receives the type of the last event generated by the target.  For a list of possible types, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff541478">DEBUG_EVENT_XXX</a>.


### -param ProcessId [out]

Receives the process ID of the process in which the event occurred.  If this information is not available, DEBUG_ANY_ID will be returned instead.


### -param ThreadId [out]

Receives the thread ID of the thread in which the last event occurred.  If this information is not available, DEBUG_ANY_ID will be returned instead.


### -param ExtraInformation [out, optional]

Receives extra information about the event.  The contents of this extra information depends on the type of the event as indicated by the returned <i>Type</i> parameter. For example, if <i>Type</i> is breakpoint, <i>ExtraInformation</i> contains a DEBUG_LAST_EVENT_INFO_BREAKPOINT; if Type is Exception, ExtraInformation contains a DEBUG_LAST_EVENT_INFO_EXCEPTION. Refer to <a href="https://msdn.microsoft.com/library/windows/hardware/ff541478">DEBUG_EVENT_XXX</a> for the complete list of event types and the dbgeng.h header file for the structure definitions for each event type. 

  If <i>ExtraInformation</i> is <b>NULL</b>, this information is not returned.


### -param ExtraInformationSize [in]

Specifies the size, in bytes, of the buffer that <i>ExtraInformation</i> specifies.


### -param ExtraInformationUsed [out, optional]

Receives the size, in bytes, of extra information.  If <i>ExtraInformationUsed</i> is <b>NULL</b>, this information is not returned.


### -param Description [out, optional]

Receives the description of the event.  If <i>Description</i> is <b>NULL</b>, this information is not returned.


### -param DescriptionSize [in]

Specifies the size, in characters, of the buffer that <i>Description</i> specifies.


### -param DescriptionUsed [out, optional]

Receives the size in characters of the description of the event.  If <i>DescriptionUsed </i>is <b>NULL</b>, this information is not returned.


## -returns



This method may also return error values.  See <a href="https://msdn.microsoft.com/713f3ee2-2f5b-415e-9908-90f5ae428b43">Return Values</a> for more details.

<table>
<tr>
<th>Return code</th>
<th>Description</th>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>S_OK</b></dt>
</dl>
</td>
<td width="60%">
The method was successful.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>S_FALSE</b></dt>
</dl>
</td>
<td width="60%">
The method was successful.  However, either <i>ExtraInformationSize</i> or <i>DescriptionSize</i> were smaller that the size of the respective data or string and the data or string was truncated to fit inside the buffer.

</td>
</tr>
</table>
 




## -remarks



For thread and process creation events, the thread ID and process ID returned to <i>ThreadId</i> and <i>ProcessId</i> are for the newly created thread or process.

For more information about the last event, see the topic <a href="https://msdn.microsoft.com/library/windows/hardware/ff543075">Event Information</a>.




## -see-also

<a href="..\dbgeng\nn-dbgeng-idebugcontrol4.md">IDebugControl4</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff548431">GetStoredEventInformation</a>



 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20IDebugControl4::GetLastEventInformationWide method%20 RELEASE:%20(1/19/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
