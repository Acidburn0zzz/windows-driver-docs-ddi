---
UID: NF:winsplp.XcvOpenPort
title: XcvOpenPort function
author: windows-driver-content
description: A port monitor server DLL's XcvOpenPort function opens a port for configuration operations.
old-location: print\xcvopenport.htm
tech.root: print
ms.assetid: ba0f5820-08eb-40c7-9593-7434ee0e29c6
ms.date: 02/02/2018
ms.keywords: print.xcvopenport, spoolfnc_d2e14d20-1b34-49f5-a627-7b08ccc79ccf.xml, winsplp/XcvOpenPort, XcvOpenPort function [Print Devices], XcvOpenPort
ms.topic: function
req.header: winsplp.h
req.include-header: Winsplp.h
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
req.lib: NtosKrnl.exe
req.dll:
req.irql:
topictype:
-	APIRef
-	kbSyntax
apitype:
-	HeaderDef
apilocation:
-	Winsplp.h
apiname:
-	XcvOpenPort
product:
- Windows
targetos: Windows
req.typenames: NOTIFICATION_CONFIG_FLAGS
req.product: Windows 10 or later.
---

# XcvOpenPort function


## -description


A port monitor server DLL's <b>XcvOpenPort</b> function opens a port for configuration operations.


## -syntax


```cpp
BOOL XcvOpenPort(
   HANDLE      hMonitor,
   LPCWSTR     pszObject,
   ACCESS_MASK GrantedAccess,
   PHANDLE     phXcv
);
```


## -parameters




### -param pszObject

Caller-supplied pointer to a string representing the name of the port. Can be <b>NULL</b>, and most monitors do not need this parameter.


### -param GrantedAccess

Caller-supplied ACCESS_MASK structure containing the access granted to the user during a print monitor UI DLL's call to the spooler's <b>OpenPrinter</b> function. See the following Remarks section.


### -param phXcv

Caller-supplied pointer to a location to receive a function-supplied port handle.


#### - hMonitor

Caller supplied monitor instance handle. This is the handle returned by the monitor's <a href="..\winsplp\nf-winsplp-initializeprintmonitor2.md">InitializePrintMonitor2</a> function. (This parameter does not exist if the print monitor supports <b>InitializePrintMonitor</b> instead of <b>InitializePrintMonitor2</b>.)


## -returns



If the operation succeeds, the function should return <b>TRUE</b>. Otherwise it should return <b>FALSE</b>.




## -remarks



Port monitor server DLLs are required to define an <b>XcvOpenPort</b> function and include its address in a <a href="..\winsplp\ns-winsplp-_monitor2.md">MONITOR2</a> structure.

The spooler's <b>OpenPrinter</b> function (described in the Microsoft Windows SDK documentation) calls <b>XcvOpenPort</b> if the specified printer name includes either of the strings "XcvPort" or "XcvMonitor". For more information, see <a href="..\winsplp\nf-winsplp-addportui.md">AddPortUI</a>.

The <b>XcvOpenPort</b> function should open the port for configuration purposes. This operation might only consist of storing the input arguments for subsequent use within <a href="..\winsplp\nf-winsplp-xcvdataport.md">XcvDataPort</a>. The function should return a handle to the stored information in the location pointed to by <i>phXcv</i>. This handle is returned to the caller of <b>OpenPrinter</b>, and subsequently received as an input argument to <b>XcvDataPort</b>.

The function should save the granted access mask. Later, when the server DLL's <b>XcvDataPort</b> function is called, the granted access should be compared with SERVER_ACCESS_ADMINISTER and if the comparison fails, <b>XcvDataPort</b> should return ERROR_ACCESS_DENIED.




## -see-also

<a href="..\winsplp\nf-winsplp-initializeprintmonitor2.md">InitializePrintMonitor2</a>



<a href="..\winsplp\nf-winsplp-xcvcloseport.md">XcvClosePort</a>



<a href="..\winsplp\nf-winsplp-xcvdataport.md">XcvDataPort</a>



<a href="..\winsplp\nf-winsplp-addportui.md">AddPortUI</a>



 

 


