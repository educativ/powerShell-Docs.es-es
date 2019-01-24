---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recursos de configuración de estado deseado integrados para Linux
ms.openlocfilehash: ea700d24c7ff4377af671944184abb3f201852e8
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048044"
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a><span data-ttu-id="c58c0-103">Recursos de configuración de estado deseado integrados para Linux</span><span class="sxs-lookup"><span data-stu-id="c58c0-103">Built-In Desired State Configuration Resources for Linux</span></span>

<span data-ttu-id="c58c0-104">Los recursos son bloques de creación que puede usar para escribir un script de configuración de estado deseado (DSC) de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c58c0-104">Resources are building blocks that you can use to write a PowerShell Desired State Configuration (DSC) script.</span></span> <span data-ttu-id="c58c0-105">DSC para Linux incorpora un conjunto de funcionalidades integradas para configurar recursos tales como archivos y carpetas, paquetes, variables de entorno, servicios y procesos.</span><span class="sxs-lookup"><span data-stu-id="c58c0-105">DSC for Linux comes with a set of built-in functionality for configuring resources such as files and folders, packages, environment variables, and services and processes.</span></span>

## <a name="built-in-resources"></a><span data-ttu-id="c58c0-106">Recursos integrados</span><span class="sxs-lookup"><span data-stu-id="c58c0-106">Built-in resources</span></span>

<span data-ttu-id="c58c0-107">En la tabla siguiente se ofrece una lista con estos recursos y vínculos a temas que los describen en detalle.</span><span class="sxs-lookup"><span data-stu-id="c58c0-107">The following table provides a list of these resources and links to topics that describe them in detail.</span></span>

* <span data-ttu-id="c58c0-108">[Recurso nxArchive](lnxArchiveResource.md): ofrece un mecanismo para desempaquetar archivos de almacenamiento (.tar, .zip) en una ruta específica.</span><span class="sxs-lookup"><span data-stu-id="c58c0-108">[nxArchive Resource](lnxArchiveResource.md)--Provides a mechanism to unpack archive (.tar, .zip) files at a specific path.</span></span>
* <span data-ttu-id="c58c0-109">[Recurso nxEnvironment](lnxEnvironmentResource.md): administra las variables de entorno en los nodos de destino.</span><span class="sxs-lookup"><span data-stu-id="c58c0-109">[nxEnvironment Resource](lnxEnvironmentResource.md)--Manages environment variables on target nodes.</span></span>
* <span data-ttu-id="c58c0-110">[Recurso nxFile](lnxFileResource.md): administra archivos y directorios de Linux.</span><span class="sxs-lookup"><span data-stu-id="c58c0-110">[nxFile Resource](lnxFileResource.md)--Manages Linux files and directories.</span></span>
* <span data-ttu-id="c58c0-111">[Recurso nxFileLine](lnxFileLineResource.md): administra líneas individuales de un archivo de Linux.</span><span class="sxs-lookup"><span data-stu-id="c58c0-111">[nxFileLine Resource](lnxFileLineResource.md)--Manages individual lines in a Linux file.</span></span>
* <span data-ttu-id="c58c0-112">[Recurso nxGroup](lnxGroupResource.md): administra grupos locales de Linux.</span><span class="sxs-lookup"><span data-stu-id="c58c0-112">[nxGroup Resource](lnxGroupResource.md)--Manages local Linux groups.</span></span>
* <span data-ttu-id="c58c0-113">[Recurso nxPackage](lnxPackageResource.md): administra paquetes en nodos de Linux.</span><span class="sxs-lookup"><span data-stu-id="c58c0-113">[nxPackage Resource](lnxPackageResource.md)--Manages packages on Linux nodes.</span></span>
* <span data-ttu-id="c58c0-114">[Recurso nxScript](lnxScriptResource.md): ejecuta scripts en nodos de destino.</span><span class="sxs-lookup"><span data-stu-id="c58c0-114">[nxScript Resource](lnxScriptResource.md)--Runs scripts on target nodes.</span></span>
* <span data-ttu-id="c58c0-115">[Recurso nxService](lnxServiceResource.md): administra servicios (demonios) de Linux.</span><span class="sxs-lookup"><span data-stu-id="c58c0-115">[nxService Resource](lnxServiceResource.md)--Manages Linux services (daemons).</span></span>
* <span data-ttu-id="c58c0-116">[Recurso nxSshAuthorizedKeys](lnxSshAuthorizedKeysResource.md): administra claves ssh públicas para un usuario de Linux.</span><span class="sxs-lookup"><span data-stu-id="c58c0-116">[nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--Manages public ssh keys for a Linux user.</span></span>
* <span data-ttu-id="c58c0-117">[Recurso nxUser](lnxUserResource.md): administra usuarios locales de Linux.</span><span class="sxs-lookup"><span data-stu-id="c58c0-117">[nxUser Resource](lnxUserResource.md)--Manages local Linux users.</span></span>