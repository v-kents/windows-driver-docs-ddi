---
UID: NF:pep_x.PEP_ACPI_INITIALIZE_MEMORY_RESOURCE
title: PEP_ACPI_INITIALIZE_MEMORY_RESOURCE function (pep_x.h)
description: Learn how the PEP_ACPI_INITIALIZE_MEMORY_RESOURCE function initializes a platform extension plug-in's (PEP) PEP_ACPI_IO_MEMORY_RESOURCE structure.
old-location: kernel\pep_acpi_initialize_memory_resource.htm
tech.root: kernel
ms.date: 04/30/2018
keywords: ["PEP_ACPI_INITIALIZE_MEMORY_RESOURCE function"]
ms.keywords: PEP_ACPI_INITIALIZE_MEMORY_RESOURCE, PEP_ACPI_INITIALIZE_MEMORY_RESOURCE function [Kernel-Mode Driver Architecture], kernel.pep_acpi_initialize_memory_resource, pepfx/PEP_ACPI_INITIALIZE_MEMORY_RESOURCE
req.header: pep_x.h
req.include-header: Pep_x.h
req.target-type: Windows
req.target-min-winverclnt: Supported starting with Windows 10.
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
targetos: Windows
req.typenames: 
f1_keywords:
 - PEP_ACPI_INITIALIZE_MEMORY_RESOURCE
 - pep_x/PEP_ACPI_INITIALIZE_MEMORY_RESOURCE
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - HeaderDef
api_location:
 - pepfx.h
api_name:
 - PEP_ACPI_INITIALIZE_MEMORY_RESOURCE
---

# PEP_ACPI_INITIALIZE_MEMORY_RESOURCE function (pep_x.h)


## -description

The <b>PEP_ACPI_INITIALIZE_MEMORY_RESOURCE</b> function initializes a platform extension plug-in's (PEP) <a href="/windows-hardware/drivers/ddi/pepfx/ns-pepfx-_pep_acpi_io_memory_resource">PEP_ACPI_IO_MEMORY_RESOURCE</a> structure.

## -parameters

### -param ReadWrite 

[in]
If true, indicates that the resource is read/write. Otherwise, it's read-only.

### -param MinimumAddress 

[in]
Specifies the minimum acceptable starting address for the IO range.

### -param MaximumAddress 

[in]
Specifies the maximum acceptable starting address for the IO range.

### -param Alignment 

[in]
Specifies the alignment granularity for the memory address assigned.

### -param MemorySize 

[in]
Specifies the number of bytes in the memory range.

### -param Resource 

[out]
A pointer to the resource. The structure behind the pointer is of type <a href="/windows-hardware/drivers/ddi/pepfx/ns-pepfx-_pep_acpi_io_memory_resource">PEP_ACPI_IO_MEMORY_RESOURCE</a>.

## -see-also

<a href="/windows-hardware/drivers/ddi/pepfx/ns-pepfx-_pep_acpi_io_memory_resource">PEP_ACPI_IO_MEMORY_RESOURCE</a>
