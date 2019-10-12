---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método SendMetaConfigurationApply
ms.openlocfilehash: b2e420bafb8ea22aea43800f6e429d3ed785d1e8
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954882"
---
# <a name="sendmetaconfigurationapply-method"></a><span data-ttu-id="deb70-103">Método SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="deb70-103">SendMetaConfigurationApply method</span></span>

<span data-ttu-id="deb70-104">Establece la configuración del Administrador de configuración local que se usa para controlar el agente de configuración.</span><span class="sxs-lookup"><span data-stu-id="deb70-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="deb70-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="deb70-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="deb70-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="deb70-106">Parameters</span></span>

<span data-ttu-id="deb70-107">*ConfigurationData* \[in\] Datos del entorno para la configuración.</span><span class="sxs-lookup"><span data-stu-id="deb70-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="deb70-108">*force* \[in\] **true** para forzar la configuración a detenerse.</span><span class="sxs-lookup"><span data-stu-id="deb70-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="deb70-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="deb70-109">Return value</span></span>

<span data-ttu-id="deb70-110">Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="deb70-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="deb70-111">Observaciones</span><span class="sxs-lookup"><span data-stu-id="deb70-111">Remarks</span></span>

<span data-ttu-id="deb70-112">Se trata de un método estático.</span><span class="sxs-lookup"><span data-stu-id="deb70-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="deb70-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="deb70-113">Requirements</span></span>

<span data-ttu-id="deb70-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="deb70-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="deb70-115">**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="deb70-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="deb70-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="deb70-116">See also</span></span>

[<span data-ttu-id="deb70-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="deb70-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)