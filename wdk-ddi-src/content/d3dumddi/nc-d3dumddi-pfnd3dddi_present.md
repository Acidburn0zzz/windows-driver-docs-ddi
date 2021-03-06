---
UID: NC:d3dumddi.PFND3DDDI_PRESENT
title: PFND3DDDI_PRESENT
author: windows-driver-content
description: The Present function notifies the user-mode display driver that an application finished rendering and requests that the driver display the source surface by either copying or flipping or that the driver perform a color-fill operation.
old-location: display\present.htm
tech.root: display
ms.assetid: e90683b4-64b6-4018-96a5-b50118df3367
ms.date: 05/10/2018
ms.keywords: PFND3DDDI_PRESENT, PFND3DDDI_PRESENT callback, Present, Present callback function [Display Devices], UserModeDisplayDriver_Functions_186fad4e-6231-4851-94ad-7296653832cc.xml, d3dumddi/Present, display.present
ms.topic: callback
req.header: d3dumddi.h
req.include-header: D3dumddi.h
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
req.irql: 
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	UserDefined
api_location:
-	d3dumddi.h
api_name:
-	Present
product:
- Windows
targetos: Windows
req.typenames: 
---

# PFND3DDDI_PRESENT callback function


## -description


The <i>Present</i> function notifies the user-mode display driver that an application finished rendering and requests that the driver display the source surface by either copying or flipping or that the driver perform a color-fill operation. 


## -parameters




### -param hDevice [in]

A handle to the display device (graphics context).


### -param *








*pData* [in]

A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543240">D3DDDIARG_PRESENT</a> structure that describes the resource to display.


## -returns



<i>Present</i> returns one of the following values:

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
The resource is successfully displayed.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b>E_OUTOFMEMORY</b></dt>
</dl>
</td>
<td width="60%">
<i>Present</i> could not allocate the required memory for it to complete.

</td>
</tr>
</table>
 




## -remarks



The Microsoft Direct3D runtime calls the user-mode display driver's <i>Present</i> function to notify the user-mode display driver that an application finished rendering and to request that the driver display out the source surface or that the driver perform a color-fill operation. If the <b>hSrcResource</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff543240">D3DDDIARG_PRESENT</a> structure that the <i>pData</i> parameter points to is non-<b>NULL</b>, <i>Present</i> requests that the user-mode display driver display new content to the screen; if <b>hSrcResource</b> is <b>NULL</b>, <i>Present</i> requests that the user-mode display driver perform a color-fill operation to the screen. 

If the <b>hDstResource</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff543240">D3DDDIARG_PRESENT</a> structure is <b>NULL</b>, the destination surface is unknown. In addition, the destination surface and a list of clipping rectangles are determined in kernel mode before sending the hardware command stream through DMA to the graphics processor. 

As a result, the user-mode display driver cannot generate hardware instructions to perform the present operation. These hardware instructions must be generated by the display miniport driver. However, when the <b>hSrcResource</b> member of D3DDDIARG_PRESENT is non-<b>NULL</b>, the user-mode display driver must derive the allocation handle to the source surface and insert this handle in the <b>hSrcAllocation</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544218">D3DDDICB_PRESENT</a> structure in a call to the <a href="https://msdn.microsoft.com/460b9be5-5817-4225-9089-f86ad64f4554">pfnPresentCb</a> function. The display miniport driver can then successfully generate the hardware instructions. The user-mode display driver typically derives the allocation handle from the resource information in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff543240">D3DDDIARG_PRESENT</a> structure.

If the <b>hDstResource</b> member of D3DDDIARG_PRESENT is non-<b>NULL</b>, the destination surface for the present is known and the user-mode display driver must fill in the <b>hDstAllocation</b> member of <a href="https://msdn.microsoft.com/library/windows/hardware/ff544218">D3DDDICB_PRESENT</a> with the corresponding allocation handle.

If a user-mode display driver exposes a DDI version of less than 0x0000000C (the driver returns this value in the <b>DriverVersion</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff541724">D3D10DDIARG_OPENADAPTER</a> structure in a call to the driver's <a href="https://msdn.microsoft.com/41dc9ee4-e9bc-4ebd-9b90-6446ded6ea16">OpenAdapter</a> function), the Direct3D runtime first calls the user-mode display driver's <a href="https://msdn.microsoft.com/library/windows/hardware/hh463886">Flush</a> function to submit any outstanding hardware commands in the command buffer before the runtime calls the user-mode display driver's <i>Present</i> function. In this way, the user-mode display driver's <i>Present</i> function is serialized with render operations (that is, calls to the <a href="https://msdn.microsoft.com/f242162e-6237-469c-b178-5a51dcf69e32">pfnRenderCb</a> function). If a user-mode display driver exposes a DDI version of 0x0000000C or greater and the calling application runs in windowed mode, the runtime also calls <i>Flush</i> before it calls <i>Present</i>. If a user-mode display driver exposes a DDI version of 0x0000000C or greater and the calling application runs in full-screen mode, the runtime will not call <i>Flush</i> before it calls <i>Present</i>. This behavior allows drivers that implement their own threading to queue present calls. A driver that exposes a DDI version of 0x0000000C or greater must call <b>pfnRenderCb</b> to internally flush any outstanding command buffers before the driver calls the <a href="https://msdn.microsoft.com/460b9be5-5817-4225-9089-f86ad64f4554">pfnPresentCb</a> function.




## -see-also




<a href="https://msdn.microsoft.com/library/windows/hardware/ff543240">D3DDDIARG_PRESENT</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff544519">D3DDDI_DEVICEFUNCS</a>



<a href="https://msdn.microsoft.com/1a46b129-1e78-44e6-a609-59eab206692b">DxgkDdiPresent</a>



<a href="https://msdn.microsoft.com/fd634768-5e1e-4f40-82fd-5ef69148c3d7">DxgkDdiRender</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/hh463886">Flush</a>



<a href="https://msdn.microsoft.com/f242162e-6237-469c-b178-5a51dcf69e32">pfnRenderCb</a>
 

 

