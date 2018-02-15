---
UID: NS:d3dkmthk._D3DKMT_OUTPUTDUPL_SNAPSHOT
title: "_D3DKMT_OUTPUTDUPL_SNAPSHOT"
author: windows-driver-content
description: Provides information on the current processes in which output duplication is occurring.
old-location: display\d3dkmt_outputdupl_snapshot.htm
old-project: display
ms.assetid: bec6a398-34e8-4c03-ac15-c3f00645eac7
ms.author: windowsdriverdev
ms.date: 12/29/2017
ms.keywords: D3DKMT_OUTPUTDUPL_SNAPSHOT, D3DKMT_OUTPUTDUPL_SNAPSHOT structure [Display Devices], d3dkmthk/D3DKMT_OUTPUTDUPL_SNAPSHOT, _D3DKMT_OUTPUTDUPL_SNAPSHOT, display.d3dkmt_outputdupl_snapshot
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: d3dkmthk.h
req.include-header: D3dkmthk.h
req.target-type: Windows
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
topictype:
-	APIRef
-	kbSyntax
apitype:
-	HeaderDef
apilocation:
-	D3dkmthk.h
apiname:
-	D3DKMT_OUTPUTDUPL_SNAPSHOT
product: Windows
targetos: Windows
req.typenames: D3DKMT_OUTPUTDUPL_SNAPSHOT
---

# _D3DKMT_OUTPUTDUPL_SNAPSHOT structure


## -description


Provides information on the current processes in which output duplication is occurring.


## -syntax


````
typedef struct _D3DKMT_OUTPUTDUPL_SNAPSHOT {
  UINT                          Size;
  UINT                          SessionProcessCount;
  UINT                          SessionActiveConnectionsCount;
  UINT                          NumVidPnSources;
  UINT                          NumOutputDuplContexts;
  OUTPUTDUPL_CONTEXT_DEBUG_INFO OutputDuplDebugInfos[];
} D3DKMT_OUTPUTDUPL_SNAPSHOT;
````


## -struct-fields




### -field Size

[in/out] The size, in bytes, of the entire structure.


### -field SessionProcessCount

[out] The number of processes in this session that are currently duplicating output. The value of <b>NumOutputDuplContexts</b> specifies the maximum possible number of processes.


### -field SessionActiveConnectionsCount

[out] The total number of active contexts in this session. The value may be more than the number of active contexts in the 2-D array, which are per adapter.


### -field NumVidPnSources

[out] The number of video present network (VidPN) sources.


### -field NumOutputDuplContexts

[out] The number of contexts in which output duplication is occurring.


### -field OutputDuplDebugInfos

Reserved for system use. Set to zero.
