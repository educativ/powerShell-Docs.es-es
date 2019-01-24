---
ms.date: 12/12/2018
keywords: DSC, powershell, recursos, la galería, el programa de instalación
title: Instalación de recursos de DSC adicionales
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402906"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="a3551-103">Instalación de recursos de DSC adicionales</span><span class="sxs-lookup"><span data-stu-id="a3551-103">Install Additional DSC Resources</span></span>

<span data-ttu-id="a3551-104">PowerShell incluye varios recursos de cuadro de Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="a3551-104">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="a3551-105">El **PSDesiredStateConfiguration** módulo contiene todos los recursos de DSC OOB disponibles en la instancia específica de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3551-105">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="a3551-106">Se trata de una lista de los recursos OOB incluidos en PowerShell 4.0 y una descripción de las capacidades del recurso.</span><span class="sxs-lookup"><span data-stu-id="a3551-106">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="a3551-107">Se trata de una lista incompleta, como el número de recursos OOB ha crecido con cada versión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3551-107">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|<span data-ttu-id="a3551-108">Recurso</span><span class="sxs-lookup"><span data-stu-id="a3551-108">Resource</span></span>  |<span data-ttu-id="a3551-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="a3551-109">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="a3551-110">**File**</span><span class="sxs-lookup"><span data-stu-id="a3551-110">**File**</span></span>|<span data-ttu-id="a3551-111">Controla el estado de los archivos y directorios.</span><span class="sxs-lookup"><span data-stu-id="a3551-111">Controls the state of files and directories.</span></span> <span data-ttu-id="a3551-112">Copia los archivos de un **origen** a un **destino** y las actualiza cuando el **origen** cambios mediante la comparación de fechas, las sumas de comprobación y algoritmos hash.</span><span class="sxs-lookup"><span data-stu-id="a3551-112">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span>|
|<span data-ttu-id="a3551-113">**Archive**</span><span class="sxs-lookup"><span data-stu-id="a3551-113">**Archive**</span></span>|<span data-ttu-id="a3551-114">Desempaqueta los archivos y una ubicación especificada.</span><span class="sxs-lookup"><span data-stu-id="a3551-114">Unpacks archives and a specified location.</span></span> <span data-ttu-id="a3551-115">Valida los archivos con un determinado **suma de comprobación**.</span><span class="sxs-lookup"><span data-stu-id="a3551-115">Validates the archives with a specified **Checksum**.</span></span>|
|<span data-ttu-id="a3551-116">**Environment**</span><span class="sxs-lookup"><span data-stu-id="a3551-116">**Environment**</span></span>|<span data-ttu-id="a3551-117">Administra las variables de entorno.</span><span class="sxs-lookup"><span data-stu-id="a3551-117">Manages environment variables.</span></span>|
|<span data-ttu-id="a3551-118">**Grupo**</span><span class="sxs-lookup"><span data-stu-id="a3551-118">**Group**</span></span>|<span data-ttu-id="a3551-119">Administra grupos locales y controla la pertenencia al grupo.</span><span class="sxs-lookup"><span data-stu-id="a3551-119">Manages local groups and controls group membership.</span></span>|
|<span data-ttu-id="a3551-120">**Log**</span><span class="sxs-lookup"><span data-stu-id="a3551-120">**Log**</span></span>|<span data-ttu-id="a3551-121">Escribe los mensajes a la `Microsoft-Windows-Desired State Configuration/Analytic` registro de eventos.</span><span class="sxs-lookup"><span data-stu-id="a3551-121">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>|
|<span data-ttu-id="a3551-122">**Package**</span><span class="sxs-lookup"><span data-stu-id="a3551-122">**Package**</span></span>|<span data-ttu-id="a3551-123">Instala o desinstala los paquetes mediante **argumentos**, **LogPath**, **ReturnCode**, otras configuraciones.</span><span class="sxs-lookup"><span data-stu-id="a3551-123">Installs or uninstalls packages using **Arguments**, **LogPath**, **ReturnCode**, other settings.</span></span>|
|<span data-ttu-id="a3551-124">**Registry**</span><span class="sxs-lookup"><span data-stu-id="a3551-124">**Registry**</span></span>|<span data-ttu-id="a3551-125">Administra los valores y claves del registro.</span><span class="sxs-lookup"><span data-stu-id="a3551-125">Manages registry keys and values.</span></span>|
|<span data-ttu-id="a3551-126">**Script**</span><span class="sxs-lookup"><span data-stu-id="a3551-126">**Script**</span></span>|<span data-ttu-id="a3551-127">Le permite diseñar su propio [get-test-set](../resources/get-test-set.md) bloques de script.</span><span class="sxs-lookup"><span data-stu-id="a3551-127">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>|
|<span data-ttu-id="a3551-128">**Service**</span><span class="sxs-lookup"><span data-stu-id="a3551-128">**Service**</span></span>|<span data-ttu-id="a3551-129">Configura los servicios de Windows.</span><span class="sxs-lookup"><span data-stu-id="a3551-129">Configures Windows services.</span></span>|
|<span data-ttu-id="a3551-130">**Usuario**</span><span class="sxs-lookup"><span data-stu-id="a3551-130">**User**</span></span> |<span data-ttu-id="a3551-131">Administra usuarios locales y los atributos.</span><span class="sxs-lookup"><span data-stu-id="a3551-131">Manages local users and attributes.</span></span>|
|<span data-ttu-id="a3551-132">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="a3551-132">**WindowsFeature**</span></span>|<span data-ttu-id="a3551-133">Administra los roles y características.</span><span class="sxs-lookup"><span data-stu-id="a3551-133">Manages roles and features.</span></span>|
|<span data-ttu-id="a3551-134">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="a3551-134">**WindowsProcess**</span></span>|<span data-ttu-id="a3551-135">Configura los procesos de Windows.</span><span class="sxs-lookup"><span data-stu-id="a3551-135">Configures Windows processes.</span></span>|

<span data-ttu-id="a3551-136">Los recursos OOB permiten un buen punto de partida para las operaciones comunes.</span><span class="sxs-lookup"><span data-stu-id="a3551-136">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="a3551-137">Si los recursos OOB no satisfacen sus necesidades, puede escribir su propio [recurso personalizado](../resources/authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="a3551-137">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="a3551-138">Antes de escribir un recurso personalizado para solucionar el problema, debe examinar el gran número de recursos de DSC que ya se han creado por Microsoft y la Comunidad de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3551-138">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="a3551-139">Puede encontrar los recursos de DSC en ambos el [Galería de PowerShell](https://www.powershellgallery.com/) y [GitHub](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="a3551-139">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="a3551-140">También puede instalar directamente desde la consola de PowerShell mediante los recursos de DSC [PowerShellGet](/powershell/module/powershellget/).</span><span class="sxs-lookup"><span data-stu-id="a3551-140">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="a3551-141">Instalación de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a3551-141">Installing PowerShellGet</span></span>

<span data-ttu-id="a3551-142">Para determinar si ya tiene **PowerShell** get o para obtener ayuda para instalarlo, consulte la guía siguiente: [instalación PowerShellGet](/powershell/gallery/installing-psget).</span><span class="sxs-lookup"><span data-stu-id="a3551-142">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="a3551-143">Buscar recursos de DSC mediante PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a3551-143">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="a3551-144">Una vez **PowerShellGet** está instalado en el sistema, puede buscar e instalar recursos de DSC hospedados en el [Galería de PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="a3551-144">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="a3551-145">En primer lugar, use el [Find-DSCResource](/powershell/module/powershellget/find-dscresource) para encontrar los recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="a3551-145">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="a3551-146">Al ejecutar `Find-DSCResource` por primera vez, verá el aviso siguiente para instalar el proveedor de NuGet"".</span><span class="sxs-lookup"><span data-stu-id="a3551-146">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

<span data-ttu-id="a3551-147">Después de presionar 'y', se instala el proveedor de "NuGet", verá una lista de recursos de DSC que se pueden instalar desde la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3551-147">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="a3551-148">No se muestra la lista porque es muy grande.</span><span class="sxs-lookup"><span data-stu-id="a3551-148">List is not shown because it is very large.</span></span>

<span data-ttu-id="a3551-149">También puede especificar el `-Name` parámetro mediante caracteres comodín, o `-Filter` parámetro sin caracteres comodín para limitar la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="a3551-149">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="a3551-150">En este ejemplo intenta encontrar un recurso de DSC "TimeZone" mediante los caracteres comodín.</span><span class="sxs-lookup"><span data-stu-id="a3551-150">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a3551-151">Actualmente no hay un error en la `Find-DSCResource` cmdlet que impida usar caracteres comodín en ambos el `-Name` y `-Filter` parámetros.</span><span class="sxs-lookup"><span data-stu-id="a3551-151">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="a3551-152">El segundo ejemplo siguiente muestra el uso de una solución alternativa `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="a3551-152">The second example below shows a workaround using `Where-Object`.</span></span>

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

<span data-ttu-id="a3551-153">También puede usar `Where-Object` para buscar recursos de DSC con filtrado más granular.</span><span class="sxs-lookup"><span data-stu-id="a3551-153">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="a3551-154">Este enfoque será más lenta que la compila en parámetros de filtrado.</span><span class="sxs-lookup"><span data-stu-id="a3551-154">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="a3551-155">Para obtener más información sobre el filtrado, consulte [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="a3551-155">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="a3551-156">Instalar recursos de DSC mediante PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a3551-156">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="a3551-157">Para instalar un recurso de DSC, use el [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, especificando el nombre del módulo que se muestra en **módulo** nombre en los resultados de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="a3551-157">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="a3551-158">El recurso de "Zona horaria" existe en el módulo "ComputerManagementDSC", por lo que es que el módulo de este ejemplo se instala.</span><span class="sxs-lookup"><span data-stu-id="a3551-158">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="a3551-159">Si no ha confiado en la Galería de PowerShell, vea la advertencia debajo de confirmación y que se le indicará cómo evitar el número de solicitudes posterior en instala.</span><span class="sxs-lookup"><span data-stu-id="a3551-159">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="a3551-160">Presione "s" para continuar con la instalación del módulo.</span><span class="sxs-lookup"><span data-stu-id="a3551-160">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="a3551-161">Después de la instalación, compruebe que el nuevo recurso está instalado mediante [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span><span class="sxs-lookup"><span data-stu-id="a3551-161">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

<span data-ttu-id="a3551-162">También puede ver otros recursos en el módulo recién instalado, especificando el `-ModuleName` parámetro.</span><span class="sxs-lookup"><span data-stu-id="a3551-162">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a><span data-ttu-id="a3551-163">Vea también</span><span class="sxs-lookup"><span data-stu-id="a3551-163">See also</span></span>

- [<span data-ttu-id="a3551-164">¿Qué son los recursos?</span><span class="sxs-lookup"><span data-stu-id="a3551-164">What are Resources?</span></span>](../resources/resources.md)