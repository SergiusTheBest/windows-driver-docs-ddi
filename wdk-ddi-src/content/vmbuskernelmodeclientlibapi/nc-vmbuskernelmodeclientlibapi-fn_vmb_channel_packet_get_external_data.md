---
UID: NC:vmbuskernelmodeclientlibapi.FN_VMB_CHANNEL_PACKET_GET_EXTERNAL_DATA
title: FN_VMB_CHANNEL_PACKET_GET_EXTERNAL_DATA
author: windows-driver-content
description: The VmbChannelPacketGetExternalData function gets any external Memory Descriptor Lists (MDLs) associated with a packet during packet processing.
ms.assetid: ccc4fa85-12fd-4491-af6e-29248f23f837
ms.author: windowsdriverdev
ms.date: 05/21/2018
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: vmbuskernelmodeclientlibapi.h
req.include-header:
req.target-type:
req.target-min-winverclnt: Windows 10, version 1803
req.target-min-winversvr:
req.kmdf-ver:
req.umdf-ver:
req.lib:
req.dll:
req.irql: 
req.ddi-compliance:
req.unicode-ansi:
req.idl:
req.max-support:
req.namespace:
req.assembly:
req.type-library: 
topic_type: 
-	apiref
api_type: 
-	UserDefined
api_location: 
-	vmbuskernelmodeclientlibapi.h
api_name: 
-	FN_VMB_CHANNEL_PACKET_GET_EXTERNAL_DATA
product:
-	Windows
targetos: Windows
---

# FN_VMB_CHANNEL_PACKET_GET_EXTERNAL_DATA callback function

## -description

<p class="CCE_Message">[Some information relates to pre-released product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.]

The <b>VmbChannelPacketGetExternalData</b>  function gets any external
Memory Descriptor Lists (MDLs) associated with a packet during packet processing. 

## -prototype

```
//Declaration

FN_VMB_CHANNEL_PACKET_GET_EXTERNAL_DATA FnVmbChannelPacketGetExternalData; 

// Definition

NTSTATUS FnVmbChannelPacketGetExternalData 
(
	VMBPACKETCOMPLETION PacketCompletionContext
	UINT32 Flags
	PMDL *Mdl
)
{...}

```

## -parameters

### -param PacketCompletionContext

A  handle that identifies the incoming packet and is used to refer to the packet
once processing is finished.

### -param Flags

Flags that control how the MDL is mapped. The possible flag values are: 

<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>
<td width="40%"><a id="VMBUS_CHANNEL_PACKET_EXTERNAL_DATA_FLAG_READ_ONLY"></a><a id="vmbus_channel_packet_external_data_flag_read_only"></a><dl>
<dt><b>VMBUS_CHANNEL_PACKET_EXTERNAL_DATA_FLAG_READ_ONLY</b></dt>
</dl>
</td>
<td width="60%">
Map MDL as read-only.

</td>
</tr>
</table>

### -param *Mdl

 A pointer to the mapped MDL.

## -returns

<b>VmbChannelPacketGetExternalData</b> returns a status code. If this function returns STATUS_PENDING,
the caller must return from the packet processing callback, which will be
called again, possibly at a different IRQL, when the external data is ready.
At this point, a call to this function will succeed and return the external
data.

## -remarks

Creating an MDL which represents the memory described by this
transaction causes these regions of the virtual machine to be pinned in memory for the remainder of the transaction lifetime.  This is what may cause the function to return STATUS_PENDING, because the regions of the
virtual machine may need to be paged in.


 The MDL returned by this function describes memory that is already
locked in place. Therefore, there is no need to call the
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554664">MmProbeAndLockPages</a> function.  The MDL will, however, have neither a user-mode virtual
address nor a kernel-mode virtual address.  If the driver that calls this function requires a virtual address to manipulate the memory within the virtual machine, that driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff554629">MmMapLockedPagesSpecifyCache</a>, or <a href="https://msdn.microsoft.com/library/windows/hardware/ff554559">MmGetSystemAddressForMdlSafe</a>,
and the corresponding unlock function later, like <a href="https://msdn.microsoft.com/library/windows/hardware/ff556391">MmUnmapLockedPages</a>.
An alternative to using a virtual address would be to just pass the MDL on down to a driver which uses it for direct memory access. 

 The driver calling this function is not required to release the MDL.  It becomes invalid upon calling the <a href="https://msdn.microsoft.com/1DC215DF-1F53-4910-84D5-17E13BE6202A">VmbChannelPacketComplete</a> function. The Kernel Mode Client Library (KMCL) later releases it.  

> [!IMPORTANT]
> This function is called through the VMBus Kernel Mode Client Library (KMCL) interface, provided by the Vmbkmcl.sys bus driver. 
>
> To access the KMCL interface, allocate a **KMCL_CLIENT_INTERFACE_V1** structure to receive the interface, then call either [**WdfFdoQueryForInterface**](../wdffdo/nf-wdffdo-wdffdoqueryforinterface.md) or [**WdfIoTargetQueryForInterface**](../wdfiotarget/nf-wdfiotarget-wdfiotargetqueryforinterface.md) with these parameters:
> 
> - *InterfaceType* parameter: **KMCL_CLIENT_INTERFACE_TYPE**
> - *Size* parameter: `sizeof(KMCL_CLIENT_INTERFACE_V1)`
> - *Version* parameter: **KMCL_CLIENT_INTERFACE_VERSION_LATEST** 
>
> If the interface query function succeeds, the **KMCL_CLIENT_INTERFACE_V1** structure contains function pointers for the VMBus KMCL functions that you can use to call them.
>
> For more information about driver-defined interfaces, see [Using Driver-Defined Interfaces](https://docs.microsoft.com/windows-hardware/drivers/wdf/using-driver-defined-interfaces).

## -see-also

<a href="https://msdn.microsoft.com/library/windows/hardware/ff554559">MmGetSystemAddressForMdlSafe</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff554629">MmMapLockedPagesSpecifyCache</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff554664">MmProbeAndLockPages</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff556391">MmUnmapLockedPages</a>



<a href="https://msdn.microsoft.com/1DC215DF-1F53-4910-84D5-17E13BE6202A">VmbChannelPacketComplete</a>