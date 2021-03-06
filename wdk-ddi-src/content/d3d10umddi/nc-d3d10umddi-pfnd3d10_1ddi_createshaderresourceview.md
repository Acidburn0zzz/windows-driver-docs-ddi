---
UID: NC:d3d10umddi.PFND3D10_1DDI_CREATESHADERRESOURCEVIEW
title: PFND3D10_1DDI_CREATESHADERRESOURCEVIEW
author: windows-driver-content
description: The CreateShaderResourceView(D3D10_1) function creates a shader resource view.
old-location: display\createshaderresourceview_d3d10_1_.htm
ms.assetid: 7a0a92d2-a5df-4bee-a950-8a89aeb3dbb8
ms.date: 05/10/2018
ms.keywords: CreateShaderResourceView_d3d10_1_, CreateShaderResourceView_d3d10_1_ callback function [Display Devices], PFND3D10_1DDI_CREATESHADERRESOURCEVIEW, PFND3D10_1DDI_CREATESHADERRESOURCEVIEW callback, UserModeDisplayDriverDx10_Functions_e8a41f3e-a247-4350-aa1d-3967ec2f903d.xml, d3d10umddi/CreateShaderResourceView_d3d10_1_, display.createshaderresourceview_d3d10_1_
ms.topic: callback
req.header: d3d10umddi.h
req.include-header: D3d10umddi.h
req.target-type: Desktop
req.target-min-winverclnt: CreateShaderResourceView(D3D10_1) is supported on Windows Vista with Service Pack 1 (SP1) and later versions and Windows Server 2008 and later versions.
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
-	d3d10umddi.h
api_name:
-	CreateShaderResourceView_d3d10_1_
product:
- Windows
targetos: Windows
tech.root: display
req.typenames: 
---

# PFND3D10_1DDI_CREATESHADERRESOURCEVIEW callback function


## -description


The <b>CreateShaderResourceView(D3D10_1)</b> function creates a shader resource view.


## -parameters




### -param Arg1

*hDevice* [in]

A handle to the display device (graphics context).

### -param *

*pCreateShaderResourceView* [in]

A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff541861">D3D10_1DDIARG_CREATESHADERRESOURCEVIEW</a> structure that describes the parameters that the user-mode display driver uses to create a shader resource view.

### -param Arg2

*hShaderResourceView* [in]

A handle to the driver's private data for the shader resource view. The driver returns the size, in bytes, of the memory region that the Microsoft Direct3D runtime must allocate for the private data from a call to the driver's <a href="https://msdn.microsoft.com/310adb3e-1af4-430e-ba50-bd145ffda361">CalcPrivateShaderResourceViewSize(D3D10_1)</a> function. The handle is really just a pointer to a region of memory, the size of which the driver requested. The driver uses this region of memory to store internal data structures that are related to its shader resource view object.

### -param Arg3

*hRTShaderResourceView* [in]

A handle to the shader resource view that the driver should use anytime it calls back into the Direct3D runtime. 



## -returns



None

The driver can use the <a href="https://msdn.microsoft.com/968b04a7-8869-410c-a6fc-83d57726858f">pfnSetErrorCb</a> callback function to set an error code. For more information about setting error codes, see the Remarks section.




## -remarks



The driver might run out of memory. Therefore, the driver can pass E_OUTOFMEMORY or D3DDDIERR_DEVICEREMOVED in a call to the <a href="https://msdn.microsoft.com/968b04a7-8869-410c-a6fc-83d57726858f">pfnSetErrorCb</a> function. The Direct3D runtime will determine that any other errors are critical. If the driver passes any errors, including D3DDDIERR_DEVICEREMOVED, the Direct3D runtime will determine that the handle is invalid; therefore, the runtime will not call the <a href="https://msdn.microsoft.com/dcdfe76e-a392-4a76-91fe-03648fec1278">DestroyShaderResourceView</a> function to destroy the handle that the <i>hShaderResourceView</i> parameter specifies.




## -see-also




<a href="https://msdn.microsoft.com/310adb3e-1af4-430e-ba50-bd145ffda361">CalcPrivateShaderResourceViewSize(D3D10_1)</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff541861">D3D10_1DDIARG_CREATESHADERRESOURCEVIEW</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff541873">D3D10_1DDI_DEVICEFUNCS</a>



<a href="https://msdn.microsoft.com/dcdfe76e-a392-4a76-91fe-03648fec1278">DestroyShaderResourceView</a>



<a href="https://msdn.microsoft.com/968b04a7-8869-410c-a6fc-83d57726858f">pfnSetErrorCb</a>
 

 

