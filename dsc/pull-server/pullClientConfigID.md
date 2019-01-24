---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Configurar un cliente de incorporación de cambios mediante identificadores de configuración en PowerShell 5.0 y versiones posteriores
ms.openlocfilehash: 8d8cf478f9127e1b7005d1b9e832e84b11612c9c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402785"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="00695-103">Configurar un cliente de incorporación de cambios mediante identificadores de configuración en PowerShell 5.0 y versiones posteriores</span><span class="sxs-lookup"><span data-stu-id="00695-103">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="00695-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="00695-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00695-105">El servidor de extracción (característica de Windows *DSC-Service*) es un componente de Windows Server admitido, si bien no está previsto ofrecer nuevas características o funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="00695-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="00695-106">Se recomienda empezar a realizar la transición de los clientes administrados a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started) (incluye características más allá del servidor de extracción de Windows Server) o a una de las soluciones de la comunidad que figuran [aquí](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="00695-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="00695-107">Antes de configurar un cliente de extracción, debe configurar un servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="00695-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="00695-108">Aunque este orden no es necesario, ayuda a solucionar problemas y le ayuda a asegurarse de que el registro fue correcto.</span><span class="sxs-lookup"><span data-stu-id="00695-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="00695-109">Para configurar un servidor de extracción, puede usar a las siguientes guías:</span><span class="sxs-lookup"><span data-stu-id="00695-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="00695-110">Configuración de un servidor de extracción SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="00695-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="00695-111">Configuración de un servidor de extracción HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="00695-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="00695-112">Cada nodo de destino puede configurarse para descargar las configuraciones, recursos e incluso notificado su estado.</span><span class="sxs-lookup"><span data-stu-id="00695-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="00695-113">Las secciones siguientes muestran cómo configurar a un cliente de extracción con un recurso compartido de SMB o el servidor de extracción de DSC de HTTP.</span><span class="sxs-lookup"><span data-stu-id="00695-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="00695-114">Cuando se actualiza el LCM del nodo, se comunicará a la ubicación configurada para descargar las configuraciones asignadas.</span><span class="sxs-lookup"><span data-stu-id="00695-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="00695-115">Si todos los recursos necesarios no existen en el nodo, se descargarán automáticamente ellos desde la ubicación configurada.</span><span class="sxs-lookup"><span data-stu-id="00695-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="00695-116">Si el nodo se configura con un [servidor de informes](reportServer.md), a continuación, notificará el estado de la operación.</span><span class="sxs-lookup"><span data-stu-id="00695-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> <span data-ttu-id="00695-117">**Nota**: En este tema se aplica a PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="00695-117">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="00695-118">Para obtener información sobre cómo configurar un cliente de incorporación de cambios en PowerShell 4.0, consulte [Configuración de un cliente de incorporación de cambios con el id. de configuración de PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="00695-118">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="00695-119">Configurar el LCM de cliente de incorporación de cambios</span><span class="sxs-lookup"><span data-stu-id="00695-119">Configure the pull client LCM</span></span>

<span data-ttu-id="00695-120">Ejecución de cualquiera de los ejemplos siguientes crea una nueva carpeta de salida denominada **PullClientConfigID** y coloca un archivo MOF de metaconfiguración en ella.</span><span class="sxs-lookup"><span data-stu-id="00695-120">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="00695-121">En este caso, el nombre del archivo MOF de metaconfiguración será `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="00695-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="00695-122">Para aplicar la configuración, llame al cmdlet **Set-DscLocalConfigurationManager**, con el valor de **Path** establecido en la ubicación del archivo MOF de metaconfiguración.</span><span class="sxs-lookup"><span data-stu-id="00695-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="00695-123">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="00695-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="00695-124">Id. de configuración</span><span class="sxs-lookup"><span data-stu-id="00695-124">Configuration ID</span></span>

<span data-ttu-id="00695-125">Los ejemplos siguientes se establece la **ConfigurationID** propiedades del LCM en un **Guid** que había creado anteriormente para este propósito.</span><span class="sxs-lookup"><span data-stu-id="00695-125">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="00695-126">La propiedad **ConfigurationID** es lo que usa el LCM para buscar la configuración adecuada en el servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="00695-126">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="00695-127">El archivo MOF de configuración del servidor de incorporación de cambios debe denominarse `ConfigurationID.mof`, donde *ConfigurationID* es el valor de la propiedad **ConfigurationID** del LCM del nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="00695-127">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="00695-128">Para obtener más información, consulte [publicar las configuraciones a un servidor de extracción (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="00695-128">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="00695-129">Puede crear uno aleatorio **Guid** en el ejemplo a continuación, o mediante el [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="00695-129">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="00695-130">Para obtener más información sobre el uso de **GUID** en su entorno, consulte [planear GUID](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="00695-130">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="00695-131">Configurar un cliente de extracción para descargar las configuraciones</span><span class="sxs-lookup"><span data-stu-id="00695-131">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="00695-132">Cada cliente debe configurarse en **extracción** modo y dada la incorporación de cambios de dirección url del servidor donde se almacena su configuración.</span><span class="sxs-lookup"><span data-stu-id="00695-132">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="00695-133">Para ello, tendrá que configurar el administrador de configuración local (LCM) con la información necesaria.</span><span class="sxs-lookup"><span data-stu-id="00695-133">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="00695-134">Para configurar el LCM, debe crear un tipo especial de configuración, decorado con el atributo **DSCLocalConfigurationManager**.</span><span class="sxs-lookup"><span data-stu-id="00695-134">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="00695-135">Para más información sobre la configuración del LCM, consulte [Configuración del administrador de configuración local](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="00695-135">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="00695-136">Servidor de extracción de DSC de HTTP</span><span class="sxs-lookup"><span data-stu-id="00695-136">HTTP DSC Pull Server</span></span>

<span data-ttu-id="00695-137">El script siguiente configura el LCM para que extraiga configuraciones de un servidor denominado "CONTOSO-PullSrv".</span><span class="sxs-lookup"><span data-stu-id="00695-137">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

<span data-ttu-id="00695-138">En el script, el bloque **ConfigurationRepositoryWeb** define el servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="00695-138">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="00695-139">El **ServerUrl** especifica la dirección url de la extracción de DSC</span><span class="sxs-lookup"><span data-stu-id="00695-139">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="00695-140">Recurso compartido de SMB</span><span class="sxs-lookup"><span data-stu-id="00695-140">SMB Share</span></span>

<span data-ttu-id="00695-141">El script siguiente configura el LCM para que extraiga configuraciones desde el recurso compartido SMB `\\SMBPullServer\Pull`.</span><span class="sxs-lookup"><span data-stu-id="00695-141">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="00695-142">En el script, el **ConfigurationRepositoryShare** bloque define el servidor de extracción, en este caso, es simplemente un recurso compartido SMB.</span><span class="sxs-lookup"><span data-stu-id="00695-142">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="00695-143">Configurar un cliente de extracción para descargar los recursos</span><span class="sxs-lookup"><span data-stu-id="00695-143">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="00695-144">Si especifica solo el **ConfigurationRepositoryWeb** o **ConfigurationRepositoryShare** bloquear en su configuración del LCM (como en los ejemplos anteriores), el cliente de extracción extraerá los recursos de la misma recupera sus configuraciones de ubicación.</span><span class="sxs-lookup"><span data-stu-id="00695-144">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="00695-145">También puede especificar ubicaciones independientes para los recursos.</span><span class="sxs-lookup"><span data-stu-id="00695-145">You can also specify separate locations for resources.</span></span> <span data-ttu-id="00695-146">Para especificar una ubicación de recursos como un servidor independiente, use el **ResourceRepositoryWeb** bloque.</span><span class="sxs-lookup"><span data-stu-id="00695-146">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="00695-147">Para especificar una ubicación de recursos como un recurso compartido SMB, use el **ResourceRepositoryShare** bloque.</span><span class="sxs-lookup"><span data-stu-id="00695-147">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="00695-148">Puede combinar **ConfigurationRepositoryWeb** con **ResourceRepositoryShare** o **ConfigurationRepositoryShare** con **ResourceRepositoryWeb** .</span><span class="sxs-lookup"><span data-stu-id="00695-148">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb**.</span></span> <span data-ttu-id="00695-149">Ejemplos de esto no se muestran a continuación.</span><span class="sxs-lookup"><span data-stu-id="00695-149">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="00695-150">Servidor de extracción de DSC de HTTP</span><span class="sxs-lookup"><span data-stu-id="00695-150">HTTP DSC Pull Server</span></span>

<span data-ttu-id="00695-151">La metaconfiguración siguiente configura un cliente de extracción para obtener sus configuraciones de **CONTOSO-PullSrv** y sus recursos de **CONTOSO-ResourceSrv**.</span><span class="sxs-lookup"><span data-stu-id="00695-151">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a><span data-ttu-id="00695-152">Recurso compartido de SMB</span><span class="sxs-lookup"><span data-stu-id="00695-152">SMB Share</span></span>

<span data-ttu-id="00695-153">El ejemplo siguiente muestra una metaconfiguration que configura un cliente para que extraiga configuraciones desde el recurso compartido SMB `\\SMBPullServer\Configurations`y los recursos desde el recurso compartido SMB `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="00695-153">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="00695-154">Descargar automáticamente los recursos en el modo de inserción</span><span class="sxs-lookup"><span data-stu-id="00695-154">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="00695-155">A partir de PowerShell 5.0, los clientes de extracción pueden descargar los módulos desde un recurso compartido SMB, incluso cuando están configurados para **Push** modo.</span><span class="sxs-lookup"><span data-stu-id="00695-155">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="00695-156">Esto es especialmente útil en escenarios donde no desea configurar un servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="00695-156">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="00695-157">El **ResourceRepositoryShare** bloque puede usarse sin especificar un **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="00695-157">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="00695-158">El ejemplo siguiente muestra una metaconfiguration que configura un cliente para obtener recursos desde un recurso compartido SMB `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="00695-158">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="00695-159">Cuando el nodo está **PUSHED** una configuración, se descargarán automáticamente los recursos necesarios, desde el recurso compartido especificado.</span><span class="sxs-lookup"><span data-stu-id="00695-159">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="00695-160">Configurar un cliente de incorporación de cambios para informar del estado</span><span class="sxs-lookup"><span data-stu-id="00695-160">Set up a Pull Client to report status</span></span>

<span data-ttu-id="00695-161">De forma predeterminada, los nodos no enviarán informes a un servidor de incorporación de cambios configurado.</span><span class="sxs-lookup"><span data-stu-id="00695-161">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="00695-162">Puede usar un solo servidor de extracción para configuraciones, recursos e informes, pero debe crear un bloque **ReportRepositoryWeb** para configurar los informes.</span><span class="sxs-lookup"><span data-stu-id="00695-162">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="00695-163">Servidor de extracción de DSC de HTTP</span><span class="sxs-lookup"><span data-stu-id="00695-163">HTTP DSC Pull Server</span></span>

<span data-ttu-id="00695-164">En el siguiente ejemplo se muestra una metaconfiguración que configura un cliente para que envíe informes de datos y extraiga configuraciones y recursos a un único servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="00695-164">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="00695-165">Para especificar un servidor de informes, utilice un bloque **ReportRepositoryWeb**.</span><span class="sxs-lookup"><span data-stu-id="00695-165">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="00695-166">Un servidor de informes no puede ser un servidor SMB.</span><span class="sxs-lookup"><span data-stu-id="00695-166">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="00695-167">La metaconfiguración siguiente configura un cliente de extracción para que obtenga sus configuraciones de **CONTOSO-PullSrv** y sus recursos de **CONTOSO-ResourceSrv**, y para que envíe los informes a **CONTOSO-ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="00695-167">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a><span data-ttu-id="00695-168">Recurso compartido de SMB</span><span class="sxs-lookup"><span data-stu-id="00695-168">SMB Share</span></span>

<span data-ttu-id="00695-169">Un servidor de informes no puede ser un recurso compartido SMB.</span><span class="sxs-lookup"><span data-stu-id="00695-169">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="00695-170">Pasos a seguir</span><span class="sxs-lookup"><span data-stu-id="00695-170">Next Steps</span></span>

<span data-ttu-id="00695-171">Una vez que se ha configurado el cliente de extracción, puede usar a las siguientes guías para realizar los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="00695-171">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="00695-172">Publicación de las configuraciones en un servidor de extracción (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="00695-172">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="00695-173">Empaquetado y carga de recursos en un servidor de extracción (v4)</span><span class="sxs-lookup"><span data-stu-id="00695-173">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="00695-174">Véase también</span><span class="sxs-lookup"><span data-stu-id="00695-174">See Also</span></span>

* [<span data-ttu-id="00695-175">Configuración de un cliente de extracción con nombres de configuración</span><span class="sxs-lookup"><span data-stu-id="00695-175">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)