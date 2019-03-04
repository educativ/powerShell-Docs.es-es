---
title: Controla el elemento de configuración (formato) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861181"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="51335-102">Elemento Controls para Configuration (formato)</span><span class="sxs-lookup"><span data-stu-id="51335-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="51335-103">Define los controles comunes que pueden usarse en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="51335-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="51335-104">Elemento de controles de configuración (formato) del elemento de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="51335-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="51335-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="51335-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="51335-106">Atributos y elementos</span><span class="sxs-lookup"><span data-stu-id="51335-106">Attributes and Elements</span></span>

<span data-ttu-id="51335-107">Las secciones siguientes describen los atributos, elementos secundarios y el elemento primario de la `Controls` elemento.</span><span class="sxs-lookup"><span data-stu-id="51335-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="51335-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="51335-108">Attributes</span></span>

<span data-ttu-id="51335-109">Ninguna.</span><span class="sxs-lookup"><span data-stu-id="51335-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="51335-110">Elementos secundarios</span><span class="sxs-lookup"><span data-stu-id="51335-110">Child Elements</span></span>

|<span data-ttu-id="51335-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="51335-111">Element</span></span>|<span data-ttu-id="51335-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="51335-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="51335-113">Elemento de control para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="51335-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="51335-114">Elemento necesario.</span><span class="sxs-lookup"><span data-stu-id="51335-114">Required element.</span></span><br /><br /> <span data-ttu-id="51335-115">Define un control común que puede usarse en todas las vistas del archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="51335-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="51335-116">Elementos primarios</span><span class="sxs-lookup"><span data-stu-id="51335-116">Parent Elements</span></span>

|<span data-ttu-id="51335-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="51335-117">Element</span></span>|<span data-ttu-id="51335-118">Descripción</span><span class="sxs-lookup"><span data-stu-id="51335-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="51335-119">Elemento de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="51335-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="51335-120">Representa el elemento de nivel superior de un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="51335-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="51335-121">Observaciones</span><span class="sxs-lookup"><span data-stu-id="51335-121">Remarks</span></span>

<span data-ttu-id="51335-122">Puede crear cualquier número de controles comunes.</span><span class="sxs-lookup"><span data-stu-id="51335-122">You can create any number of common controls.</span></span> <span data-ttu-id="51335-123">Para cada control, debe especificar el nombre que se usa para hacer referencia el control y los componentes del control.</span><span class="sxs-lookup"><span data-stu-id="51335-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="51335-124">Véase también</span><span class="sxs-lookup"><span data-stu-id="51335-124">See Also</span></span>

[<span data-ttu-id="51335-125">Elemento de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="51335-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="51335-126">Elemento de control para los controles de configuración (formato)</span><span class="sxs-lookup"><span data-stu-id="51335-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="51335-127">Escribir un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="51335-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)