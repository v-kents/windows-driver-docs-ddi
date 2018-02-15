---
UID: NI:ehstorbandmgmt.IOCTL_EHSTOR_BANDMGMT_CREATE_BAND
title: IOCTL_EHSTOR_BANDMGMT_CREATE_BAND
author: windows-driver-content
description: New bands are created on a band-managed storage device with the IOCTL_EHSTOR_BANDMGMT_CREATE_BAND request. A new band is added to the table of band entries, which includes band location and security properties.
old-location: storage\ioctl_ehstor_bandmgmt_create_band.htm
old-project: storage
ms.assetid: B5AEA98A-223D-4D14-A36B-EB5266F80AF8
ms.author: windowsdriverdev
ms.date: 1/10/2018
ms.keywords: storage.ioctl_ehstor_bandmgmt_create_band, IOCTL_EHSTOR_BANDMGMT_CREATE_BAND control code [Storage Devices], IOCTL_EHSTOR_BANDMGMT_CREATE_BAND, ehstorbandmgmt/IOCTL_EHSTOR_BANDMGMT_CREATE_BAND
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: ioctl
req.header: ehstorbandmgmt.h
req.include-header: EhStorBandMgmt.h
req.target-type: Windows
req.target-min-winverclnt: Available starting with Windows 8
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
topictype:
-	APIRef
-	kbSyntax
apitype:
-	HeaderDef
apilocation:
-	EhStorBandMgmt.h
apiname:
-	IOCTL_EHSTOR_BANDMGMT_CREATE_BAND
product: Windows
targetos: Windows
req.typenames: DXVA_VideoSample32
---

# IOCTL_EHSTOR_BANDMGMT_CREATE_BAND IOCTL


##  Major Code: 


[[XREF-LINK:IRP_MJ_DEVICE_CONTROL]

## -description


New bands are created on a band-managed storage device with the <b>IOCTL_EHSTOR_BANDMGMT_CREATE_BAND</b> request. A new band is added to the table of band entries, which includes band location and security properties.


## -ioctlparameters




### -input-buffer

The buffer at <i>Irp-&gt;AssociatedIrp.SystemBuffer</i> must contain an <a href="..\ehstorbandmgmt\ns-ehstorbandmgmt-_create_band_parameters.md">CREATE_BAND_PARAMETERS</a> structure followed by the <a href="..\ehstorbandmgmt\ns-ehstorbandmgmt-_band_location_info.md">BAND_LOCATION_INFO</a>, <a href="..\ehstorbandmgmt\ns-ehstorbandmgmt-_band_security_info.md">BAND_SECURITY_INFO</a>, and <b>AUTH_KEY</b> structures. 

If the <b>AuthKeyOffset</b> member of <a href="..\ehstorbandmgmt\ns-ehstorbandmgmt-_create_band_parameters.md">CREATE_BAND_PARAMETERS</a> is set to <b>EHSTOR_BANDMGR_NO_KEY</b>, the input data in the system buffer need not include an <b>AUTH_KEY</b> structure.


### -input-buffer-length

<i>Parameters.DeviceIoControl.InputBufferLength</i> indicates the size, in bytes, of the buffer, which must be at least <b>sizeof</b> (CREATE_BAND_PARAMETERS)   +  <b>sizeof</b>(BAND_LOCATION_INFO) +   <b> sizeof</b> (BAND_SECURITY_INFO)   + <b>sizeof</b>(AUTH_KEY).


### -output-buffer

The output buffer at <i>Irp-&gt;AssociatedIrp.SystemBuffer</i> optionally contains a ULONG value for the identifier of the newly created band.  


### -output-buffer-length

<i>Parameters.DeviceIoControl.OutputBufferLength</i> must be at least <b>sizeof</b>(ULONG) to receive the band identifier. If return of the band identifier is not wanted, set <i>Parameters.DeviceIoControl.OutputBufferLength</i> to 0.


### -in-out-buffer



<text></text>




### -inout-buffer-length



<text></text>




### -status-block

One of the following values can be returned in the <b>Status</b> field.

<table>
<tr>
<th>Status Value</th>
<th>Description</th>
</tr>
<tr>
<td>STATUS_SUCCESS</td>
<td>The new band was created.</td>
</tr>
<tr>
<td>STATUS_INVALID_DEVICE_REQUEST</td>
<td>The storage device does not support band management.</td>
</tr>
<tr>
<td>STATUS_INVALID_BUFFER_SIZE</td>
<td>The input buffer size is invalid.</td>
</tr>
<tr>
<td>STATUS_INVALID_PARAMETER</td>
<td>Information in the input buffer is invalid.</td>
</tr>
<tr>
<td>STATUS_CONFLICTING_ADDRESSES</td>
<td>The band was not created due to overlapping locations.</td>
</tr>
<tr>
<td>STATUS_INSUFFICIENT_RESOURCES</td>
<td>The band was not created because the band table is already full.</td>
</tr>
<tr>
<td>STATUS_IO_DEVICE_ERROR</td>
<td>Communication failed. The storage device might be incompatible with security protocols. </td>
</tr>
</table>
 


## -remarks



Assigning an authentication key to a newly created band is optional. If no key is provided, where  <b>AuthKeyOffset</b> = <b>EHSTOR_BANDMGR_NO_KEY</b> in the <a href="..\ehstorbandmgmt\ns-ehstorbandmgmt-_create_band_parameters.md">CREATE_BAND_PARAMETERS</a> structure, a default authentication key is used. However, this leaves the band vulnerable to another caller who may take control over the band immediately after its creation by changing its authentication key. It is recommended to assign a non-default authentication key to the band at creation time.

The changes made to the band table by this request are committed to the device atomically before the IOCTL request completes. Therefore, it is guaranteed that the band is created with all of its properties set or not created at all should a system or power failure occur.

The location of the new band must not overlap with an existing band or this request will fail with STATUS_CONFLICTING_ADDRESSES.

If the band is unlocked, either  the <b>ReadLock</b> or <b>WriteLock</b> members of <a href="..\ehstorbandmgmt\ns-ehstorbandmgmt-_band_security_info.md">BAND_SECURITY_INFO</a> are set to FALSE, and <b>CREATEBAND_AUTHKEY_CACHING_ENABLED</b> is set in the <b>Flags</b> member of <a href="..\ehstorbandmgmt\ns-ehstorbandmgmt-_create_band_parameters.md">CREATE_BAND_PARAMETERS</a>, then credential caching is enabled. The authentication silo driver will cache the band authentication key in memory. This allows the silo driver  to automatically authenticate host access to the storage device when volume maintenance is required, such as resizing the band.




## -see-also

<a href="..\ehstorbandmgmt\ns-ehstorbandmgmt-_create_band_parameters.md">CREATE_BAND_PARAMETERS</a>



<a href="..\ehstorbandmgmt\ns-ehstorbandmgmt-_band_security_info.md">BAND_SECURITY_INFO</a>



<a href="..\ehstorbandmgmt\ns-ehstorbandmgmt-_band_location_info.md">BAND_LOCATION_INFO</a>



 

 

<a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [storage\storage]:%20IOCTL_EHSTOR_BANDMGMT_CREATE_BAND control code%20 RELEASE:%20(1/10/2018)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a>
