---
title: Elemento EntrySelectedBy para WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363334"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="abe4c-102">Elemento EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="abe4c-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="abe4c-103">Define los tipos de .NET que usan esta definición de la vista amplia o la condición que debe existir para que se use esta definición.</span><span class="sxs-lookup"><span data-stu-id="abe4c-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="abe4c-104">Elemento Configuration (Format) elemento ViewDefinitions (Format) elemento View (Format) elemento WideControl (Format) elemento WideEntries (Format) WideEntry (Format) elemento EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="abe4c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="abe4c-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="abe4c-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="abe4c-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="abe4c-106">Attributes and Elements</span></span>

<span data-ttu-id="abe4c-107">En las secciones siguientes se describen los atributos, los elementos secundarios y el elemento primario del elemento `EntrySelectedBy`.</span><span class="sxs-lookup"><span data-stu-id="abe4c-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="abe4c-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="abe4c-108">Attributes</span></span>

<span data-ttu-id="abe4c-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="abe4c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="abe4c-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="abe4c-110">Child Elements</span></span>

|<span data-ttu-id="abe4c-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="abe4c-111">Element</span></span>|<span data-ttu-id="abe4c-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="abe4c-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="abe4c-113">Elemento SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="abe4c-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="abe4c-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="abe4c-114">Optional element.</span></span><br /><br /> <span data-ttu-id="abe4c-115">Define la condición que debe existir para que se use esta definición de vista ancha.</span><span class="sxs-lookup"><span data-stu-id="abe4c-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="abe4c-116">Elemento SelectionSetName para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="abe4c-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="abe4c-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="abe4c-117">Optional element.</span></span><br /><br /> <span data-ttu-id="abe4c-118">Especifica un conjunto de tipos de .NET que usan esta definición de vista ancha.</span><span class="sxs-lookup"><span data-stu-id="abe4c-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="abe4c-119">Elemento TypeName para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="abe4c-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="abe4c-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="abe4c-120">Optional element.</span></span><br /><br /> <span data-ttu-id="abe4c-121">Especifica un tipo .NET que usa esta definición de vista ancha.</span><span class="sxs-lookup"><span data-stu-id="abe4c-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="abe4c-122">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="abe4c-122">Parent Elements</span></span>

|<span data-ttu-id="abe4c-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="abe4c-123">Element</span></span>|<span data-ttu-id="abe4c-124">Descripción</span><span class="sxs-lookup"><span data-stu-id="abe4c-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="abe4c-125">Elemento WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="abe4c-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="abe4c-126">Proporciona una definición de la vista amplia.</span><span class="sxs-lookup"><span data-stu-id="abe4c-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="abe4c-127">Observaciones</span><span class="sxs-lookup"><span data-stu-id="abe4c-127">Remarks</span></span>

<span data-ttu-id="abe4c-128">Debe especificar al menos un tipo, conjunto de selección o condición de selección para una definición de vista ancha.</span><span class="sxs-lookup"><span data-stu-id="abe4c-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="abe4c-129">No hay ningún límite máximo para el número de elementos secundarios que puede usar.</span><span class="sxs-lookup"><span data-stu-id="abe4c-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="abe4c-130">Las condiciones de selección se usan para definir una condición que debe existir para la definición que se va a usar, por ejemplo, cuando un objeto tiene una propiedad concreta o un valor de propiedad o un valor de script específicos se evalúa como `true`.</span><span class="sxs-lookup"><span data-stu-id="abe4c-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="abe4c-131">Para obtener más información sobre las condiciones de selección, consulte [definir condiciones para Mostrar datos](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="abe4c-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="abe4c-132">Para obtener más información sobre otros componentes de una vista amplia, vea [crear una vista amplia](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="abe4c-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="abe4c-133">Véase también</span><span class="sxs-lookup"><span data-stu-id="abe4c-133">See Also</span></span>

[<span data-ttu-id="abe4c-134">Elemento WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="abe4c-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="abe4c-135">Elemento SelectionCondition para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="abe4c-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="abe4c-136">Elemento SelectionSetName para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="abe4c-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="abe4c-137">Elemento TypeName para EntrySelectedBy para WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="abe4c-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="abe4c-138">Crear una vista amplia</span><span class="sxs-lookup"><span data-stu-id="abe4c-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="abe4c-139">Definir condiciones para Mostrar datos</span><span class="sxs-lookup"><span data-stu-id="abe4c-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="abe4c-140">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="abe4c-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
