---
UID: NS:ksmedia.SYSAUDIO_SELECT_GRAPH
title: SYSAUDIO_SELECT_GRAPH
author: windows-driver-content
description: The SYSAUDIO_SELECT_GRAPH structure is used to specify a graph that includes an optional node such as an AEC control.
old-location: audio\sysaudio_select_graph.htm
tech.root: audio
ms.assetid: f114e8ef-4fb7-4fdd-9c83-d8e74c91190e
ms.date: 05/08/2018
ms.keywords: "*PSYSAUDIO_SELECT_GRAPH, PSYSAUDIO_SELECT_GRAPH, PSYSAUDIO_SELECT_GRAPH structure pointer [Audio Devices], SYSAUDIO_SELECT_GRAPH, SYSAUDIO_SELECT_GRAPH structure [Audio Devices], aud-prop_9dd94d88-2ed4-4908-ac6e-eb1a82ea152d.xml, audio.sysaudio_select_graph, ksmedia/PSYSAUDIO_SELECT_GRAPH, ksmedia/SYSAUDIO_SELECT_GRAPH"
ms.topic: struct
req.header: ksmedia.h
req.include-header: Ksmedia.h
req.target-type: Windows
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
-	HeaderDef
api_location:
-	ksmedia.h
api_name:
-	SYSAUDIO_SELECT_GRAPH
product:
- Windows
targetos: Windows
req.typenames: SYSAUDIO_SELECT_GRAPH, *PSYSAUDIO_SELECT_GRAPH
---

# SYSAUDIO_SELECT_GRAPH structure


## -description


The SYSAUDIO_SELECT_GRAPH structure is used to specify a graph that includes an optional node such as an AEC control.


## -struct-fields




### -field Property

Specifies the property to get or set. This parameter is a structure of type <a href="https://msdn.microsoft.com/library/windows/hardware/ff564262">KSPROPERTY</a>.


### -field PinId

Specifies the SysAudio starting pin ID for the graph.


### -field NodeId

Specifies the SysAudio node ID to be included in the graph.


### -field Flags

No flag bits are defined. Set to zero.


### -field Reserved

Reserved. Set to zero. 


## -see-also




<a href="https://msdn.microsoft.com/library/windows/hardware/ff564262">KSPROPERTY</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff537428">KSPROPERTY_SYSAUDIO_SELECT_GRAPH</a>
 

 

