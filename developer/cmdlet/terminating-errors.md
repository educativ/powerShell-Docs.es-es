---
title: La terminación | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b804e738-aefa-41bb-9649-f9ed897fd96c
caps.latest.revision: 8
ms.openlocfilehash: c593da1f7bdb6ddf09ba8d5de92af730687dbc8a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859241"
---
# <a name="terminating-errors"></a><span data-ttu-id="6afb8-102">Errores de terminación</span><span class="sxs-lookup"><span data-stu-id="6afb8-102">Terminating Errors</span></span>

<span data-ttu-id="6afb8-103">Este tema describe el método utilizado para la terminación del informe.</span><span class="sxs-lookup"><span data-stu-id="6afb8-103">This topic discusses the method used to report terminating errors.</span></span> <span data-ttu-id="6afb8-104">También se explica cómo llamar al método desde el cmdlet y describe las excepciones que se pueden devolver el tiempo de ejecución de Windows PowerShell cuando se llama al método.</span><span class="sxs-lookup"><span data-stu-id="6afb8-104">It also discusses how to call the method from within the cmdlet, and it discusses the exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="6afb8-105">Cuando un carácter de terminación se produce error, el cmdlet debe informar del error mediante una llamada a la [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) método.</span><span class="sxs-lookup"><span data-stu-id="6afb8-105">When a terminating error occurs, the cmdlet should report the error by calling the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method.</span></span> <span data-ttu-id="6afb8-106">Este método permite al cmdlet enviar un registro de error que describe la condición que provocó el error de terminación.</span><span class="sxs-lookup"><span data-stu-id="6afb8-106">This method allows the cmdlet to send an error record that describes the condition that caused the terminating error.</span></span> <span data-ttu-id="6afb8-107">Para obtener más información acerca de los registros de error, consulte [registros de Error de Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="6afb8-107">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="6afb8-108">Cuando el [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) se llama al método, el tiempo de ejecución de Windows PowerShell detiene la ejecución de la canalización de forma permanente y produce una [ System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) excepción.</span><span class="sxs-lookup"><span data-stu-id="6afb8-108">When the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method is called, the  Windows PowerShell runtime permanently stops the execution of the pipeline and throws a [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) exception.</span></span> <span data-ttu-id="6afb8-109">Todos los intentos posteriores para llamar a [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError), o varias otra API hace que las llamadas a producir un [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) excepción.</span><span class="sxs-lookup"><span data-stu-id="6afb8-109">Any subsequent attempts to call [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError), or several other APIs causes those calls to throw a [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) exception.</span></span>

<span data-ttu-id="6afb8-110">El [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) excepción puede producirse también si otro cmdlet en la canalización notifica un error de terminación, si el usuario solicitó detener la canalización, o si se ha detenido la canalización antes de la finalización por cualquier motivo.</span><span class="sxs-lookup"><span data-stu-id="6afb8-110">The [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) exception can also occur if another cmdlet in the pipeline reports a terminating error, if the user has asked to stop the pipeline, or if the pipeline has been halted before completion for any reason.</span></span> <span data-ttu-id="6afb8-111">El cmdlet no es necesario detectar la [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) excepción a menos que debe abrir limpiar los recursos o su estado interno.</span><span class="sxs-lookup"><span data-stu-id="6afb8-111">The cmdlet does not need to catch the [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) exception unless it must clean up open resources or its internal state.</span></span>

<span data-ttu-id="6afb8-112">Cmdlets puede escribir cualquier número de objetos de salida o errores de no terminación antes de informar de un error de terminación.</span><span class="sxs-lookup"><span data-stu-id="6afb8-112">Cmdlets can write any number of output objects or non-terminating errors before reporting a terminating error.</span></span> <span data-ttu-id="6afb8-113">Sin embargo, el error de terminación permanentemente detiene la canalización y ningún resultado más, la terminación, o se pueden notificar errores de no terminación.</span><span class="sxs-lookup"><span data-stu-id="6afb8-113">However, the terminating error permanently stops the pipeline, and no further output, terminating errors, or non-terminating errors can be reported.</span></span>

<span data-ttu-id="6afb8-114">Puede llamar los cmdlets [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) solo desde el subproceso que llama el [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), o [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="6afb8-114">Cmdlets can call [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) only from the thread that called the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="6afb8-115">No intente llamar a [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) o [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) desde otro subproceso.</span><span class="sxs-lookup"><span data-stu-id="6afb8-115">Do not attempt to call [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) or [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="6afb8-116">En su lugar, se deben comunicar errores hacia el subproceso principal.</span><span class="sxs-lookup"><span data-stu-id="6afb8-116">Instead, errors must be communicated back to the main thread.</span></span>

<span data-ttu-id="6afb8-117">Es posible que un cmdlet producir una excepción en su implementación de la [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), o [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método.</span><span class="sxs-lookup"><span data-stu-id="6afb8-117">It is possible for a cmdlet to throw an exception in its implementation of the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="6afb8-118">Las excepciones producidas desde estos métodos (salvo algunas condiciones de error grave que detenga el host de Windows PowerShell) se interpretan como un error de terminación que detiene la canalización, pero no de Windows PowerShell como un todo.</span><span class="sxs-lookup"><span data-stu-id="6afb8-118">Any exception thrown from these methods (except for a few severe error conditions that stop the Windows PowerShell host) is interpreted as a terminating error which stops the pipeline, but not Windows PowerShell as a whole.</span></span> <span data-ttu-id="6afb8-119">(Esto se aplica sólo al subproceso principal del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6afb8-119">(This applies only to the main cmdlet thread.</span></span> <span data-ttu-id="6afb8-120">Las excepciones no detectadas en los subprocesos generados por el cmdlet, en general, detenga el host de Windows PowerShell.) Se recomienda que use [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) en lugar de producir una excepción porque el registro de error proporciona información adicional sobre la condición de error, lo que resulta útil para el usuario final.</span><span class="sxs-lookup"><span data-stu-id="6afb8-120">Uncaught exceptions in threads spawned by the cmdlet, in general, halt the Windows PowerShell host.) We recommend that you use [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) rather than throwing an exception because the error record provides additional information about the error condition, which is useful to the end-user.</span></span> <span data-ttu-id="6afb8-121">Los cmdlets debe respetar las directrices de código administrado frente a detectar y controlar todas las excepciones (`catch (Exception e)`).</span><span class="sxs-lookup"><span data-stu-id="6afb8-121">Cmdlets should honor the managed code guideline against catching and handling all exceptions (`catch (Exception e)`).</span></span> <span data-ttu-id="6afb8-122">Convertir sólo las excepciones de tipos conocidos y esperados en los registros de errores.</span><span class="sxs-lookup"><span data-stu-id="6afb8-122">Convert only exceptions of known and expected types into error records.</span></span>

## <a name="see-also"></a><span data-ttu-id="6afb8-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="6afb8-123">See Also</span></span>

[<span data-ttu-id="6afb8-124">System.Management.Automation.Cmdlet.Beginprocessing\*</span><span class="sxs-lookup"><span data-stu-id="6afb8-124">System.Management.Automation.Cmdlet.Beginprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="6afb8-125">System.Management.Automation.Cmdlet.Endprocessing\*</span><span class="sxs-lookup"><span data-stu-id="6afb8-125">System.Management.Automation.Cmdlet.Endprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="6afb8-126">System.Management.Automation.Cmdlet.Processrecord\*</span><span class="sxs-lookup"><span data-stu-id="6afb8-126">System.Management.Automation.Cmdlet.Processrecord\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="6afb8-127">System.Management.Automation.Pipelinestoppedexception</span><span class="sxs-lookup"><span data-stu-id="6afb8-127">System.Management.Automation.Pipelinestoppedexception</span></span>](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[<span data-ttu-id="6afb8-128">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span><span class="sxs-lookup"><span data-stu-id="6afb8-128">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="6afb8-129">System.Management.Automation.Cmdlet.Writeerror\*</span><span class="sxs-lookup"><span data-stu-id="6afb8-129">System.Management.Automation.Cmdlet.Writeerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="6afb8-130">Registros de errores de PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="6afb8-130">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="6afb8-131">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6afb8-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)