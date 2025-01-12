---
UID: NF:ks.KsDeviceRegisterAggregatedClientUnknown
title: KsDeviceRegisterAggregatedClientUnknown function (ks.h)
description: TThe KsDeviceRegisterAggregatedClientUnknown function is an inline function that is a wrapper for KsRegisterAggregatedClientUnknown.
old-location: stream\ksdeviceregisteraggregatedclientunknown.htm
tech.root: stream
ms.date: 04/23/2018
keywords: ["KsDeviceRegisterAggregatedClientUnknown function"]
ms.keywords: KsDeviceRegisterAggregatedClientUnknown, KsDeviceRegisterAggregatedClientUnknown function [Streaming Media Devices], avfunc_3e7aa517-80e8-498c-939d-1769393479fb.xml, ks/KsDeviceRegisterAggregatedClientUnknown, stream.ksdeviceregisteraggregatedclientunknown
req.header: ks.h
req.include-header: Ks.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Microsoft Windows XP and later operating systems and DirectX 8.0 and later DirectX versions.
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
req.lib: 
req.dll: 
req.irql: 
targetos: Windows
req.typenames: 
f1_keywords:
 - KsDeviceRegisterAggregatedClientUnknown
 - ks/KsDeviceRegisterAggregatedClientUnknown
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - HeaderDef
api_location:
 - ks.h
api_name:
 - KsDeviceRegisterAggregatedClientUnknown
---

# KsDeviceRegisterAggregatedClientUnknown function


## -description

This inline function is a wrapper for <a href="/windows-hardware/drivers/ddi/ks/nf-ks-ksregisteraggregatedclientunknown">KsRegisterAggregatedClientUnknown</a>.

## -parameters

### -param Device 

[in]
A pointer to a <a href="/windows-hardware/drivers/ddi/ks/ns-ks-_ksdevice">KSDEVICE</a> structure representing the specified AVStream device.

### -param ClientUnknown 

[in]
A pointer to the client's undelegated <b>IUnknown</b> interface.

## -returns

Returns the newly created aggregate object.

## -remarks

This inline function performs a typecast and then calls <a href="/windows-hardware/drivers/ddi/ks/nf-ks-ksregisteraggregatedclientunknown">KsRegisterAggregatedClientUnknown</a>.

## -see-also

<a href="/windows-hardware/drivers/ddi/ks/nf-ks-ksregisteraggregatedclientunknown">KsRegisterAggregatedClientUnknown</a>
