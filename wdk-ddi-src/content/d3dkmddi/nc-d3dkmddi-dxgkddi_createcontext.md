---
UID: NC:d3dkmddi.DXGKDDI_CREATECONTEXT
title: DXGKDDI_CREATECONTEXT
author: windows-driver-content
description: The DxgkDdiCreateContext function creates a graphics processing unit (GPU) context.
old-location: display\dxgkddicreatecontext.htm
ms.assetid: aea21a36-f3d5-4541-bd2d-aa026668c562
ms.date: 05/10/2018
ms.keywords: DXGKDDI_CREATECONTEXT, DXGKDDI_CREATECONTEXT callback, DmFunctions_b1519a67-52c0-4432-9059-ef1c98f075b6.xml, DxgkDdiCreateContext, DxgkDdiCreateContext callback function [Display Devices], d3dkmddi/DxgkDdiCreateContext, display.dxgkddicreatecontext
ms.topic: callback
req.header: d3dkmddi.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
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
req.irql: PASSIVE_LEVEL
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	UserDefined
api_location:
-	d3dkmddi.h
api_name:
-	DxgkDdiCreateContext
product:
- Windows
targetos: Windows
tech.root: display
req.typenames: 
---

# DXGKDDI_CREATECONTEXT callback function


## -description


The <i>DxgkDdiCreateContext</i> function creates a graphics processing unit (GPU) context. 


## -parameters




### -param hDevice [in]

[in] A handle to the graphics context device that the new context is created on. The display miniport driver's <a href="https://msdn.microsoft.com/a7027735-0ec4-4fad-81fb-1c3aca4ebf2d">DxgkDdiCreateDevice</a> function previously provided this handle to the Microsoft DirectX graphics kernel subsystem in the <b>hDevice</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff557570">DXGKARG_CREATEDEVICE</a> structure. 


### -param pCreateContext [in, out]

[in/out] A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff557567">DXGKARG_CREATECONTEXT</a> structure that contains information about creating the context.


## -returns



<i>DxgkDdiCreateContext</i> returns one of the following values:

<table>
<tr>
<th>Return code</th>
<th>Description</th>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl>
</td>
<td width="60%">
<i>DxgkDdiCreateContext</i> successfully created the context.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>STATUS_NO_MEMORY</b></dt>
</dl>
</td>
<td width="60%">
<i>DxgkDdiCreateContext</i> could not allocate memory that was required for it to complete.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>STATUS_GRAPHICS_DRIVER_MISMATCH</b></dt>
</dl>
</td>
<td width="60%">
The display miniport driver is not compatible with the user-mode display driver that initiated the call to <i>DxgkDdiCreateContext</i>. 

</td>
</tr>
</table>
 




## -remarks



A driver uses a GPU context to hold a collection of rendering state. 

A single process can create multiple contexts on a given device. 

The driver must support an arbitrary number of contexts. The only valid reason why a driver could not create a context is if system memory runs out. 

Typically, each context can reference any resource that was previously created for the device that owns that context. 

<i>DxgkDdiCreateContext</i> should be made pageable.




## -see-also




<a href="https://msdn.microsoft.com/library/windows/hardware/ff557567">DXGKARG_CREATECONTEXT</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff557570">DXGKARG_CREATEDEVICE</a>



<a href="https://msdn.microsoft.com/a7027735-0ec4-4fad-81fb-1c3aca4ebf2d">DxgkDdiCreateDevice</a>
 

 

