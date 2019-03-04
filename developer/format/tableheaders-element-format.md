---
title: Elemento TableHeaders (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856881"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="e64ff-102">Elemento TableHeaders (formato)</span><span class="sxs-lookup"><span data-stu-id="e64ff-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="e64ff-103">Define los encabezados de las columnas de una tabla.</span><span class="sxs-lookup"><span data-stu-id="e64ff-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="e64ff-104">Elemento ViewDefinitions (formato) vista elemento (formato) TableControl (formato) TableHeaders elemento para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="e64ff-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e64ff-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e64ff-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="e64ff-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="e64ff-106">Attributes and Elements</span></span>

<span data-ttu-id="e64ff-107">Las secciones siguientes describen los atributos, elementos secundarios y elementos primarios de la `TableHeaders` elemento.</span><span class="sxs-lookup"><span data-stu-id="e64ff-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="e64ff-108">Debe haber un elemento secundario para cada propiedad del objeto que se va a mostrarse.</span><span class="sxs-lookup"><span data-stu-id="e64ff-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="e64ff-109">La información de encabezado de columna se muestra en el orden en que se especifican los elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="e64ff-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="e64ff-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="e64ff-110">Attributes</span></span>

<span data-ttu-id="e64ff-111">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="e64ff-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e64ff-112">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="e64ff-112">Child Elements</span></span>

|<span data-ttu-id="e64ff-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="e64ff-113">Element</span></span>|<span data-ttu-id="e64ff-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="e64ff-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e64ff-115">Elemento TableColumnHeader (formato)</span><span class="sxs-lookup"><span data-stu-id="e64ff-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="e64ff-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e64ff-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e64ff-117">Define la etiqueta, el ancho y la alineación de los datos para una columna de una vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="e64ff-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e64ff-118">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="e64ff-118">Parent Elements</span></span>

|<span data-ttu-id="e64ff-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="e64ff-119">Element</span></span>|<span data-ttu-id="e64ff-120">Descripción</span><span class="sxs-lookup"><span data-stu-id="e64ff-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e64ff-121">Elemento TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="e64ff-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="e64ff-122">Define un formato de tabla para obtener una vista.</span><span class="sxs-lookup"><span data-stu-id="e64ff-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e64ff-123">Observaciones</span><span class="sxs-lookup"><span data-stu-id="e64ff-123">Remarks</span></span>

<span data-ttu-id="e64ff-124">Para obtener más información acerca de los componentes de una vista de tabla, vea [crear una vista de tabla](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="e64ff-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e64ff-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e64ff-125">Example</span></span>

<span data-ttu-id="e64ff-126">Este ejemplo se muestra un `TableHeaders` elemento que define dos encabezados de columna.</span><span class="sxs-lookup"><span data-stu-id="e64ff-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
  <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a><span data-ttu-id="e64ff-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="e64ff-127">See Also</span></span>

[<span data-ttu-id="e64ff-128">Creación de una vista de tabla</span><span class="sxs-lookup"><span data-stu-id="e64ff-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e64ff-129">Elemento TableColumnHeader (formato)</span><span class="sxs-lookup"><span data-stu-id="e64ff-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="e64ff-130">Elemento TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="e64ff-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="e64ff-131">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e64ff-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)