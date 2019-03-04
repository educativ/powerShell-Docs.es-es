---
title: Ejemplo StopProcessSample02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 213ca1a4-e9fe-4969-b7d0-2fca070c6142
caps.latest.revision: 10
ms.openlocfilehash: 57751e74c9b8ab897dd35ca1fef4704d92a3f218
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863081"
---
# <a name="stopprocesssample02-sample"></a><span data-ttu-id="8de9a-102">Ejemplo StopProcessSample02</span><span class="sxs-lookup"><span data-stu-id="8de9a-102">StopProcessSample02 Sample</span></span>

<span data-ttu-id="8de9a-103">Este ejemplo muestra cómo escribir un cmdlet que escribe los mensajes de advertencia (WriteWarning), detallado (WriteVerbose) y depuración (WriteDebug) al detener los procesos en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="8de9a-103">This sample shows how to write a cmdlet that writes debug (WriteDebug), verbose (WriteVerbose), and warning (WriteWarning) messages while stopping processes on the local computer.</span></span> <span data-ttu-id="8de9a-104">Este cmdlet es similar a la `Stop-Process` cmdlet proporcionado por Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="8de9a-104">This cmdlet is similar to the `Stop-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

### <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="8de9a-105">Cómo generar el ejemplo mediante Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8de9a-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="8de9a-106">Abra Windows Internet Explorer y desplácese al directorio StopProcessSample02 bajo el directorio de ejemplos.</span><span class="sxs-lookup"><span data-stu-id="8de9a-106">Open Windows Internet Explorer and navigate to the StopProcessSample02 directory under the Samples directory.</span></span>

    <span data-ttu-id="8de9a-107">Con Windows PowerShell 2.0 instalado el SDK, vaya a la carpeta StopProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="8de9a-107">With the Windows PowerShell 2.0 SDK installed, navigate to the StopProcessSample02 folder.</span></span> <span data-ttu-id="8de9a-108">La ubicación predeterminada es C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="8de9a-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample02.</span></span>

2. <span data-ttu-id="8de9a-109">Haga doble clic en el icono del archivo de solución (.sln).</span><span class="sxs-lookup"><span data-stu-id="8de9a-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="8de9a-110">Se abre el proyecto de ejemplo en Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8de9a-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="8de9a-111">En el **compilar** menú, seleccione **compilar solución**.</span><span class="sxs-lookup"><span data-stu-id="8de9a-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="8de9a-112">En las carpetas \bin o \bin\debug de forma predeterminada, se compilará la biblioteca para el ejemplo.</span><span class="sxs-lookup"><span data-stu-id="8de9a-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="8de9a-113">Cómo ejecutar el ejemplo</span><span class="sxs-lookup"><span data-stu-id="8de9a-113">How to run the sample</span></span>

1. <span data-ttu-id="8de9a-114">Cree la siguiente carpeta del módulo:</span><span class="sxs-lookup"><span data-stu-id="8de9a-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/StopProcessSample02`

2. <span data-ttu-id="8de9a-115">Copie el ensamblado de ejemplo en la carpeta del módulo.</span><span class="sxs-lookup"><span data-stu-id="8de9a-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="8de9a-116">Inicie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8de9a-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="8de9a-117">Ejecute el siguiente comando para cargar el ensamblado en Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8de9a-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module stopprossessample02`

5. <span data-ttu-id="8de9a-118">Ejecute el siguiente comando para ejecutar el cmdlet:</span><span class="sxs-lookup"><span data-stu-id="8de9a-118">Run the following command to run the cmdlet:</span></span>

    `stop-proc`

## <a name="requirements"></a><span data-ttu-id="8de9a-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8de9a-119">Requirements</span></span>

<span data-ttu-id="8de9a-120">Este ejemplo requiere Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="8de9a-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="8de9a-121">Demostraciones</span><span class="sxs-lookup"><span data-stu-id="8de9a-121">Demonstrates</span></span>

<span data-ttu-id="8de9a-122">Este ejemplo muestra lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="8de9a-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="8de9a-123">Declarar una clase de cmdlet mediante el atributo de Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8de9a-123">Declaring a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="8de9a-124">Declarar parámetros de un cmdlet con el atributo de parámetro.</span><span class="sxs-lookup"><span data-stu-id="8de9a-124">Declaring a cmdlet parameters by using the Parameter attribute.</span></span>

- <span data-ttu-id="8de9a-125">Escribir los mensajes detallados.</span><span class="sxs-lookup"><span data-stu-id="8de9a-125">Writing verbose messages.</span></span> <span data-ttu-id="8de9a-126">Para obtener más información acerca del método utilizado para escribir los mensajes detallados, consulte [System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span><span class="sxs-lookup"><span data-stu-id="8de9a-126">For more information about the method used to write verbose messages, see [System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

- <span data-ttu-id="8de9a-127">Escribir mensajes de error.</span><span class="sxs-lookup"><span data-stu-id="8de9a-127">Writing error messages.</span></span> <span data-ttu-id="8de9a-128">Para obtener más información acerca del método utilizado para escribir mensajes de error, consulte [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError).</span><span class="sxs-lookup"><span data-stu-id="8de9a-128">For more information about the method used to write error messages, see [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError).</span></span>

- <span data-ttu-id="8de9a-129">Escribir mensajes de advertencia.</span><span class="sxs-lookup"><span data-stu-id="8de9a-129">Writing warning messages.</span></span> <span data-ttu-id="8de9a-130">Para obtener más información acerca del método utilizado para escribir mensajes de advertencia, consulte [System.Management.Automation.Cmdlet.Writewarning\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning).</span><span class="sxs-lookup"><span data-stu-id="8de9a-130">For more information about the method used to write warning messages, see [System.Management.Automation.Cmdlet.Writewarning\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning).</span></span>

## <a name="example"></a><span data-ttu-id="8de9a-131">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8de9a-131">Example</span></span>

<span data-ttu-id="8de9a-132">En este ejemplo se muestra cómo escribir mensajes de advertencia y de debug, verbose, utilizando el `WriteDebug`, `WriteVerbose`, y `WriteWarning` métodos.</span><span class="sxs-lookup"><span data-stu-id="8de9a-132">This sample shows how to write debug, verbose, and warning messages by using the `WriteDebug`, `WriteVerbose`, and `WriteWarning` methods.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Collections;
using Win32Exception = System.ComponentModel.Win32Exception;
using System.Management.Automation;             //Windows PowerShell namespace
using System.Globalization;

namespace Microsoft.Samples.PowerShell.Commands
{
   #region StopProcCommand

    /// <summary>
   /// This class implements the stop-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsLifecycle.Stop, "Proc",
       SupportsShouldProcess = true)]
   public class StopProcCommand : Cmdlet
   {
       #region Parameters

      /// <summary>
      /// This parameter provides the list of process names on
      /// which the Stop-Proc cmdlet will work.
      /// </summary>
       [Parameter(
          Position = 0,
          Mandatory = true,
          ValueFromPipeline = true,
          ValueFromPipelineByPropertyName = true
       )]
       public string[] Name
       {
          get { return processNames; }
          set { processNames = value; }
       }
       private string[] processNames;

       /// <summary>
       /// This parameter overrides the ShouldContinue call to force
       /// the cmdlet to stop its operation. This parameter should always
       /// be used with caution.
       /// </summary>
       [Parameter]
       public SwitchParameter Force
       {
           get { return force; }
           set { force = value; }
       }
       private bool force;

       /// <summary>
       /// This parameter indicates that the cmdlet should return
       /// an object to the pipeline after the processing has been
       /// completed.
       /// </summary>
       [Parameter]
       public SwitchParameter PassThru
       {
           get { return passThru; }
           set { passThru = value; }
       }
       private bool passThru;

       #endregion Parameters

       #region Cmdlet Overrides

       /// <summary>
       /// The ProcessRecord method does the following for each of the
       /// requested process names:
       /// 1) Check that the process is not a critical process.
       /// 2) Attempt to stop that process.
       /// If no process is requested then nothing occurs.
       /// </summary>
       protected override void ProcessRecord()
       {
           foreach (string name in processNames)
           {
               string message = null;

               // For every process name passed to the cmdlet, get the associated
               // processes.
               // Write a nonterminating error for failure to retrieve
               // a process.

               // Write a user-friendly verbose message to the pipeline. These
               // messages are intended to give the user detailed information
               // on the operations performed by the cmdlet. These messages will
               // appear with the -Verbose option.
               message = String.Format(CultureInfo.CurrentCulture,
                              "Attempting to stop process \"{0}\".", name);
               WriteVerbose(message);

               Process[] processes;

               try
               {
                   processes = Process.GetProcessesByName(name);
               }
               catch (InvalidOperationException ioe)
               {
                   WriteError(new ErrorRecord(ioe,
                                     "UnableToAccessProcessByName",
                                         ErrorCategory.InvalidOperation,
                                             name));
                   continue;
               }

               // Try to stop the processes that have been retrieved.
               foreach (Process process in processes)
               {
                   string processName;

                   try
                   {
                       processName = process.ProcessName;
                   }
                   catch (Win32Exception e)
                   {
                       WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                                         ErrorCategory.ObjectNotFound, process));
                       continue;
                   }

                   // Write a debug message to the host that can be used when
                   // troubleshooting a problem. All debug messages will appear
                   // with the -Debug option.
                   message = String.Format(CultureInfo.CurrentCulture,
                                 "Acquired name for pid {0} : \"{1}\"",
                                        process.Id, processName);
                   WriteDebug(message);

                   // Confirm the operation first.
                   // This is always false if the WhatIf parameter is specified.
                   if (!ShouldProcess(string.Format(CultureInfo.CurrentCulture,
                                        "{0} ({1})",
                                            processName, process.Id)))
                   {
                       continue;
                   }

                   // Make sure that the user really wants to stop a critical
                   // process that can possibly stop the computer.
                   bool criticalProcess = criticalProcessNames.Contains(processName.ToLower(CultureInfo.CurrentCulture));

                   if (criticalProcess && !force)
                   {
                       message = String.Format(CultureInfo.CurrentCulture,
                                    "The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                                        processName);

                       // It is possible that the ProcessRecord method is called
                       // multiple times when objects are recieved as inputs from
                       // the pipeline. So to retain YesToAll and NoToAll input that
                       // the user may enter across mutilple calls to this function,
                       // they are stored as private members of the cmdlet.
                       if (!ShouldContinue(message, "Warning!",
                                    ref yesToAll, ref noToAll))
                       {
                           continue;
                       }
                   } // if (criticalProcess...

                   // Display a warning message if the cmdlet is stopping a
                   // critical process.
                   if (criticalProcess)
                   {
                       message = String.Format(CultureInfo.CurrentCulture,
                                     "Stopping the critical process \"{0}\".",
                                          processName);
                       WriteWarning(message);
                   } // if (criticalProcess...

                   // Stop the named process.
                   try
                   {
                       process.Kill();
                   }
                   catch (Exception e)
                   {
                       if ((e is Win32Exception) || (e is SystemException) ||
                           (e is InvalidOperationException))
                       {
                           // This process could not be stopped so write
                           // a nonterminating error.
                           WriteError(new ErrorRecord(
                                            e,
                                            "CouldNotStopProcess",
                                            ErrorCategory.CloseError,
                                            process)
                                      );
                           continue;
                       } // if ((e is...
                           else throw;
                   } // catch

                   message = String.Format(CultureInfo.CurrentCulture,
                                  "Stopped process \"{0}\", pid {1}.",
                                        processName, process.Id);

                   WriteVerbose(message);

                   // If the PassThru parameter is specified,
                   // return the terminated process object to the pipeline.
                   if (passThru)
                   {
                       message = String.Format(CultureInfo.CurrentCulture,
                                     "Writing process \"{0}\" to pipeline",
                                          processName);
                       WriteDebug(message);
                       WriteObject(process);
                   } // if (passThru...
               } // foreach (Process...
            } // foreach (string...
        } // ProcessRecord

       #endregion Cmdlet Overrides

       #region Private Data

       private bool yesToAll, noToAll;

       /// <summary>
       /// Partial list of critical processes that should not be
       /// stopped.  Lower case is used for case insensitive matching.
       /// </summary>
       private ArrayList criticalProcessNames = new ArrayList(
          new string[] { "system", "winlogon", "spoolsv" }
       );

       #endregion Private Data

   } // StopProcCommand

   #endregion StopProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="8de9a-133">Véase también</span><span class="sxs-lookup"><span data-stu-id="8de9a-133">See Also</span></span>

[<span data-ttu-id="8de9a-134">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8de9a-134">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)