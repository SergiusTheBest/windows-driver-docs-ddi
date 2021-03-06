---
UID: NF:extension.NetExtensionGetData
title: NetExtensionGetData function (extension.h)
description: The NetExtensionGetData method retrieves packet extension data for a net packet.
tech.root: netvista
ms.assetid: D2B02C1E-3BF1-4380-8D59-C93FAF811CC8
ms.date: 02/06/2019
ms.topic: function
f1_keywords:
 - "extension/SOUNDDETECTOR_PATTERNHEADER"
ms.keywords: NetExtensionGetData
req.header: extension.h
req.include-header: netadaptercx.h
req.target-type: Universal
req.target-min-winverclnt:
req.target-min-winversvr:
req.kmdf-ver: 1.29
req.umdf-ver:
req.lib:
req.dll:
req.irql: Any level as long as target memory is resident
req.ddi-compliance:
req.unicode-ansi:
req.idl:
req.max-support:
req.namespace:
req.assembly:
req.type-library: 
topictype: 
- apiref
apitype: 
- DllExport
apilocation: 
- NtosKrnl.exe
apiname: 
- NetExtensionGetData
product:
- Windows
targetos: Windows

---

# NetExtensionGetData function


## -description
> [!WARNING]
> Some information in this topic relates to prereleased product, which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.
>
> NetAdapterCx is preview only in Windows 10, version 1903.

The **NetExtensionGetData** method retrieves packet extension data for a net packet.

## -parameters

### -param Extension

A pointer to a [**NET_EXTENSION**](../extension/ns-extension-_net_extension.md) structure that describes the requested extension information for this packet queue. 

### -param Index

The index in the packet ring for the target [**NET_PACKET**](../packet/ns-packet-_net_packet.md).

## -returns

Returns a pointer to the structure that holds the extension information for this packet.

## -remarks

Client drivers should not call this method directly. Instead, they should call the appropriate wrapper method for the type of extension they are getting:

- For checksum offload information, the client driver calls [**NetExtensionGetPacketChecksum**](../checksum/nf-checksum-netextensiongetpacketchecksum.md).
- For Large Send Offload (LSO) information, the client driver calls [**NetExtensionGetPacketLargeSendSegmentation**](../lso/nf-lso-netextensiongetpacketlargesendsegmentation.md).
- For Receive Segment Coalescence (RSC) offload information, the client driver calls [**NetExtensionGetPacketReceiveSegmentCoalescence**](../rsc/nf-rsc-netextensiongetpacketreceivesegmentcoalescence.md).


## -see-aextension

[Packet descriptors and extensions](https://docs.microsoft.com/windows-hardware/drivers/netcx/packet-descriptors-and-extensions)

[Transmit and receive queues](https://docs.microsoft.com/windows-hardware/drivers/netcx/transmit-and-receive-queues)

[**NetExtensionGetPacketChecksum**](../checksum/nf-checksum-netextensiongetpacketchecksum.md)

[**NetExtensionGetPacketLargeSendSegmentation**](../lso/nf-lso-netextensiongetpacketlargesendsegmentation.md)

[**NetExtensionGetPacketReceiveSegmentCoalescence**](../rsc/nf-rsc-netextensiongetpacketreceivesegmentcoalescence.md)
