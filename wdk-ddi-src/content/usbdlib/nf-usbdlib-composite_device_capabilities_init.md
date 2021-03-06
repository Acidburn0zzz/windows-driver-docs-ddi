---
UID: NF:usbdlib.COMPOSITE_DEVICE_CAPABILITIES_INIT
title: COMPOSITE_DEVICE_CAPABILITIES_INIT function
author: windows-driver-content
description: The COMPOSITE_DEVICE_CAPABILITIES_INIT macro initializes the COMPOSITE_DEVICE_CAPABILITIES structure.
old-location: buses\composite_driver_capabilities_init.htm
tech.root: usbref
ms.assetid: 92DDF65E-4B5B-443A-9C90-3B1BB2DD3CAF
ms.date: 05/07/2018
ms.keywords: COMPOSITE_DEVICE_CAPABILITIES_INIT, COMPOSITE_DEVICE_CAPABILITIES_INIT routine [Buses], buses.composite_driver_capabilities_init, usbdlib/COMPOSITE_DEVICE_CAPABILITIES_INIT
ms.topic: function
req.header: usbdlib.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: Requires WDK for Windows 8. Targets Windows Vista and later versions of the Windows operating system.
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
req.lib: Usbdex.lib
req.dll: 
req.irql: "<=DISPATCH_LEVEL"
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	LibDef
api_location:
-	Usbdex.lib
-	Usbdex.dll
api_name:
-	COMPOSITE_DEVICE_CAPABILITIES_INIT
product:
- Windows
targetos: Windows
req.typenames: 
---

# COMPOSITE_DEVICE_CAPABILITIES_INIT function


## -description


The <b>COMPOSITE_DEVICE_CAPABILITIES_INIT</b> macro initializes the <a href="https://msdn.microsoft.com/3C1BF8C6-3489-4636-9B3F-B0C2C1327466">COMPOSITE_DEVICE_CAPABILITIES</a> structure.


## -parameters




### -param CapabilityFlags

 A pointer to a caller-allocated <a href="https://msdn.microsoft.com/3C1BF8C6-3489-4636-9B3F-B0C2C1327466">COMPOSITE_DEVICE_CAPABILITIES</a> structure to be initialized. The macro sets the <b>CompositeDriverCapabilityFunctionSuspend</b>
member of <b>COMPOSITE_DEVICE_CAPABILITIES</b> to 0.


## -returns



This routine does not return a value.




## -see-also




<a href="https://msdn.microsoft.com/3C1BF8C6-3489-4636-9B3F-B0C2C1327466">COMPOSITE_DEVICE_CAPABILITIES</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/hh450897">How to Register a Composite Device</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/hh450898">REGISTER_COMPOSITE_DEVICE</a>
 

 

