---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso nxService de DSC para Linux
ms.openlocfilehash: fe8043995205649378725f2ab0a78e19313739c9
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047553"
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="49946-103">Recurso nxService de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="49946-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="49946-104">El recurso **nxService** de la configuración de estado deseado (DSC) de PowerShell ofrece un mecanismo para administrar servicios en un nodo de Linux.</span><span class="sxs-lookup"><span data-stu-id="49946-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="49946-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="49946-105">Syntax</span></span>

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="49946-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="49946-106">Properties</span></span>

| <span data-ttu-id="49946-107">Propiedad</span><span class="sxs-lookup"><span data-stu-id="49946-107">Property</span></span> | <span data-ttu-id="49946-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="49946-108">Description</span></span> |
|---|---|
| <span data-ttu-id="49946-109">Nombre</span><span class="sxs-lookup"><span data-stu-id="49946-109">Name</span></span>| <span data-ttu-id="49946-110">El nombre del servicio o el demonio que se configurará.</span><span class="sxs-lookup"><span data-stu-id="49946-110">The name of the service/daemon to configure.</span></span>|
| <span data-ttu-id="49946-111">Controlador</span><span class="sxs-lookup"><span data-stu-id="49946-111">Controller</span></span>| <span data-ttu-id="49946-112">El tipo de controlador de servicio que se debe usar al configurar el servicio.</span><span class="sxs-lookup"><span data-stu-id="49946-112">The type of service controller to use when configuring the service.</span></span>|
| <span data-ttu-id="49946-113">Habilitada</span><span class="sxs-lookup"><span data-stu-id="49946-113">Enabled</span></span>| <span data-ttu-id="49946-114">Indica si el servicio se inicia en el arranque.</span><span class="sxs-lookup"><span data-stu-id="49946-114">Indicates whether the service starts on boot.</span></span>|
| <span data-ttu-id="49946-115">Estado</span><span class="sxs-lookup"><span data-stu-id="49946-115">State</span></span>| <span data-ttu-id="49946-116">Indica si el servicio se está ejecutando.</span><span class="sxs-lookup"><span data-stu-id="49946-116">Indicates whether the service is running.</span></span> <span data-ttu-id="49946-117">Establezca esta propiedad en "Stopped" para garantizar que el servicio no se esté ejecutando.</span><span class="sxs-lookup"><span data-stu-id="49946-117">Set this property to "Stopped" to ensure that the service is not running.</span></span> <span data-ttu-id="49946-118">Establézcala en "Running" para garantizar que el servicio no se esté ejecutando.</span><span class="sxs-lookup"><span data-stu-id="49946-118">Set it to "Running" to ensure that the service is not running.</span></span>|
| <span data-ttu-id="49946-119">DependsOn</span><span class="sxs-lookup"><span data-stu-id="49946-119">DependsOn</span></span> | <span data-ttu-id="49946-120">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="49946-120">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="49946-121">Por ejemplo, si el elemento **ID** del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="49946-121">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="49946-122">Información adicional</span><span class="sxs-lookup"><span data-stu-id="49946-122">Additional Information</span></span>

<span data-ttu-id="49946-123">El recurso **nxService** no creará una definición de servicio ni un script para el servicio si no existe.</span><span class="sxs-lookup"><span data-stu-id="49946-123">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="49946-124">Puede usar el recurso **nxFile** de la configuración de estado deseado de PowerShell para administrar la existencia o el contenido del script o el archivo de definición del servicio.</span><span class="sxs-lookup"><span data-stu-id="49946-124">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="49946-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="49946-125">Example</span></span>

<span data-ttu-id="49946-126">En el ejemplo siguiente se muestra la configuración del servicio "httpd" (para el servidor HTTP Apache), registrado con el controlador de servicio **SystemD**.</span><span class="sxs-lookup"><span data-stu-id="49946-126">The following example shows configuration of the 'httpd' service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```