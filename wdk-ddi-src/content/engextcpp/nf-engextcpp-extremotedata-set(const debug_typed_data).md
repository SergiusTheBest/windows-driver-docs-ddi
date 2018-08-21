---
UID: NF:engextcpp.ExtRemoteData.Set(const DEBUG_TYPED_DATA)
title: ExtRemoteData::Set(const DEBUG_TYPED_DATA)
author: windows-driver-content
description: The Set method sets the region of the target's memory represented by the ExtRemoteData object.
old-location: debugger\extremotedata_set_typed.htm
tech.root: debugger
ms.assetid: a335f881-7b6f-4069-87fe-c036867b0c77
ms.author: windowsdriverdev
ms.date: 5/3/2018
ms.keywords: ExtRemoteData class [Windows Debugging],Set method, ExtRemoteData.Set, ExtRemoteData.Set(const DEBUG_TYPED_DATA), ExtRemoteData.Set(const DEBUG_TYPED_DATA*), ExtRemoteData::Set, ExtRemoteData::Set(const DEBUG_TYPED_DATA), Set, Set method [Windows Debugging], Set method [Windows Debugging],ExtRemoteData class, debugger.extremotedata_set_typed
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: method
req.header: engextcpp.hpp
req.include-header: Engextcpp.hpp
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
req.lib: 
req.dll: 
req.irql: 
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	COM
api_location:
-	engextcpp.hpp
api_name:
-	ExtRemoteData.Set
product:
-	Windows
targetos: Windows
req.typenames: 
---

# ExtRemoteData::Set(const DEBUG_TYPED_DATA)


## -description


The <b>Set</b> method sets the region of the target's memory represented by the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544008">ExtRemoteData</a> object.


## -parameters




### -param Typed [in]

Specifies the region of memory by using a <a href="https://msdn.microsoft.com/library/windows/hardware/ff541706">DEBUG_TYPED_DATA</a> structure.


## -returns



This method does not return a value.




## -remarks



The <b>Set</b> method will read the contents of the specified region of  memory and cache the data.  The data can be retrieved using <a href="https://msdn.microsoft.com/library/windows/hardware/ff544019">ExtRemoteData::GetData</a> or one of the ExtRemoteTyped::Get<i>Xxx</i> methods.




## -see-also




<a href="https://msdn.microsoft.com/library/windows/hardware/ff544008">ExtRemoteData</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff544006">ExtRemoteData::ExtRemoteData</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff544019">ExtRemoteData::GetData</a>



<a href="https://msdn.microsoft.com/50b4bee4-3a8c-45a1-9a3f-b416aa8a19e5">ExtRemoteData::Set (Offset, Bytes)</a>
 

 
