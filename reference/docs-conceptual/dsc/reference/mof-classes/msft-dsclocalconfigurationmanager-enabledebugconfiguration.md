---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método EnableDebugConfiguration
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953442"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="b5690-103">Método EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="b5690-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="b5690-104">Habilita la depuración de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="b5690-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="b5690-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b5690-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="b5690-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b5690-106">Parameters</span></span>

<span data-ttu-id="b5690-107">*BreakAll* \[in\] Establece un punto de interrupción en cada línea del script de recursos.</span><span class="sxs-lookup"><span data-stu-id="b5690-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="b5690-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="b5690-108">Return value</span></span>

<span data-ttu-id="b5690-109">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="b5690-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5690-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b5690-110">Remarks</span></span>

<span data-ttu-id="b5690-111">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="b5690-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b5690-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b5690-112">Requirements</span></span>

<span data-ttu-id="b5690-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b5690-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b5690-114">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b5690-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b5690-115">Vea también</span><span class="sxs-lookup"><span data-stu-id="b5690-115">See also</span></span>

[<span data-ttu-id="b5690-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b5690-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)