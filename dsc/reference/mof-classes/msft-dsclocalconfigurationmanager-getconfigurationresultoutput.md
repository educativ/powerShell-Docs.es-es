---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método GetConfigurationResultOutput de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048012"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b0550-103">Método GetConfigurationResultOutput de la clase MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b0550-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b0550-104">Obtiene la salida del agente de configuración asociada con un trabajo específico.</span><span class="sxs-lookup"><span data-stu-id="b0550-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="b0550-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b0550-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="b0550-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b0550-106">Parameters</span></span>

<span data-ttu-id="b0550-107">*jobId* \[in\] Identificador del trabajo del que quiere obtener datos de salida.</span><span class="sxs-lookup"><span data-stu-id="b0550-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="b0550-108">*resumeOutputBookmark* \[in\] Especifica que la salida debe ser una continuación de un marcador anterior.</span><span class="sxs-lookup"><span data-stu-id="b0550-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="b0550-109">*output* \[out\] Salida del trabajo especificado.</span><span class="sxs-lookup"><span data-stu-id="b0550-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="b0550-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="b0550-110">Return value</span></span>

<span data-ttu-id="b0550-111">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="b0550-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b0550-112">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b0550-112">Remarks</span></span>

<span data-ttu-id="b0550-113">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="b0550-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b0550-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b0550-114">Requirements</span></span>

<span data-ttu-id="b0550-115">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b0550-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b0550-116">Espacio de nombres {0} Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b0550-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b0550-117">Vea también</span><span class="sxs-lookup"><span data-stu-id="b0550-117">See also</span></span>

[<span data-ttu-id="b0550-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b0550-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)