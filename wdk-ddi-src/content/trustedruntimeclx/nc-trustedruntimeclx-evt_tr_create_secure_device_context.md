---
UID: NC:trustedruntimeclx.EVT_TR_CREATE_SECURE_DEVICE_CONTEXT
title: EVT_TR_CREATE_SECURE_DEVICE_CONTEXT
author: windows-driver-content
description: 
ms.assetid: d75797b3-0670-4a27-84b9-72359631cade
ms.date: 10/19/2018
ms.topic: callback
req.header: trustedruntimeclx.h
req.include-header:
req.target-type:
req.target-min-winverclnt:
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
-	trustedruntimeclx.h
api_name: 
-	EVT_TR_CREATE_SECURE_DEVICE_CONTEXT
product:
-	Windows
targetos: Windows
---

# EVT_TR_CREATE_SECURE_DEVICE_CONTEXT callback function

## -description

 

## -prototype

```cpp
//Declaration

EVT_TR_CREATE_SECURE_DEVICE_CONTEXT EvtTrCreateSecureDeviceContext; 

// Definition

NTSTATUS EvtTrCreateSecureDeviceContext 
(
	WDFDEVICE ServiceDevice
)
{...}

```

## -parameters

### -param ServiceDevice: 



## -returns


Return STATUS_SUCCESS if the operation succeeds. Otherwise, return an appropriate NTSTATUS values error code. For more information, see [NTSTATUS Values](https://docs.microsoft.com/windows-hardware/drivers/kernel/ntstatus-values).

## -remarks




## -see-also
