---
title: StopProcessSample04 código de ejemplo (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 48019ceb-0aeb-4cd1-8b42-79f2c29c3e65
caps.latest.revision: 5
ms.openlocfilehash: 616fb571caa4b6830a7cfe9794d0334ee8108653
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854101"
---
# <a name="stopprocesssample04-vbnet-sample-code"></a><span data-ttu-id="dedc6-102">Código de ejemplo StopProcessSample04 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="dedc6-102">StopProcessSample04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="dedc6-103">Este es el código de ejemplo VB.NET completando para el cmdlet de ejemplo StopProc04.</span><span class="sxs-lookup"><span data-stu-id="dedc6-103">Here is the complete VB.NET sample code for the StopProc04 sample cmdlet.</span></span> <span data-ttu-id="dedc6-104">Este es el código para el `Stop-Process` cmdlet se describe en [agregar conjuntos de parámetros a un Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="dedc6-104">This is the code for the `Stop-Process` cmdlet described in [Adding Parameter Sets to a Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).</span></span> <span data-ttu-id="dedc6-105">El `Stop-Process` cmdlet está diseñado para detener los procesos que se recuperan mediante el cmdlet Get-Proc (se describe en [crear su primer Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="dedc6-105">The `Stop-Process` cmdlet is designed to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="dedc6-106">Puede descargar el archivo de código fuente VB.NET (stopprocesssample04.vb) para este cmdlet Stop-Proc usando el Microsoft Windows Software Development Kit para Windows Vista y .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="dedc6-106">You can download the VB.NET (stopprocesssample04.vb) source file for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="dedc6-107">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="dedc6-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="dedc6-108">Puede descargar el archivo de código fuente VB.NET (stopprocesssample04.vb) para este cmdlet Stop-Proc usando el Microsoft Windows Software Development Kit para Windows Vista y .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="dedc6-108">You can download the VB.NET (stopprocesssample04.vb) source file for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="dedc6-109">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="dedc6-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="dedc6-110">Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="dedc6-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

```vb
Imports System
Imports System.Diagnostics
Imports System.Collections
Imports Win32Exception = System.ComponentModel.Win32Exception
Imports System.Management.Automation 'Windows PowerShell namespace
Imports System.ComponentModel
Imports System.Globalization

Namespace Microsoft.Samples.PowerShell.Commands

    ' This sample introduces parameter sets, the input object and
    ' DefaultParameterSet.
#Region "StopProcCommand"

    ''' <summary>
    ''' Class that implements the stop-proc cmdlet.
    ''' </summary>
    <Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
    SupportsShouldProcess:=True)> _
    Public Class StopProcCommand
        Inherits PSCmdlet
#Region "Parameters"

        ''' <summary>
        ''' The list of process names on which this cmdlet will work.
        ''' </summary>

        <Parameter(Position:=0, ParameterSetName:="ProcessName", _
        Mandatory:=True, _
        ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
        HelpMessage:="The name of one or more processes to stop. " & _
            "Wildcards are permitted."), [Alias]("ProcessName")> _
        Public Property Name() As String()
            Get
                Return processNames
            End Get
            Set(ByVal value As String())
                processNames = value
            End Set
        End Property
        Private processNames() As String

        ''' <summary>
        ''' Overrides the ShouldContinue check to force stop operation.
        ''' This option should always be used with caution.
        ''' </summary>

        <Parameter()> _
        Public Property Force() As SwitchParameter
            Get
                Return myForce
            End Get
            Set(ByVal value As SwitchParameter)
                myForce = value
            End Set
        End Property
        Private myForce As Boolean

        ''' <summary>
        ''' Common parameter to determine if the process should pass the
        ''' object down the pipeline after the process has been stopped.
        ''' </summary>

        <Parameter( _
        HelpMessage:= _
           "If set the process(es) will be passed to the pipeline " & _
           "after stopping them.")> _
        Public Property PassThru() As SwitchParameter
            Get
                Return myPassThru
            End Get
            Set(ByVal value As SwitchParameter)
                myPassThru = value
            End Set
        End Property
        Private myPassThru As Boolean

        ''' <summary>
        ''' The list of process IDs on which this cmdlet will work.
        ''' </summary>

        <Parameter(ParameterSetName:="ProcessId", _
        Mandatory:=True, _
        ValueFromPipelineByPropertyName:=True, _
        ValueFromPipeline:=True), [Alias]("ProcessId")> _
        Public Property Id() As Integer()
            Get
                Return processIds
            End Get
            Set(ByVal value As Integer())
                processIds = value
            End Set
        End Property
        Private processIds() As Integer

        ''' <summary>
        ''' An array of Process objects from the stream to stop.
        ''' </summary>
        ''' <value>Process objects</value>
        <Parameter(ParameterSetName:="InputObject", _
        Mandatory:=True, ValueFromPipeline:=True)> _
        Public Property InputObject() As Process()
            Get
                Return myInputObject
            End Get
            Set(ByVal value As Process())
                myInputObject = value
            End Set
        End Property
        Private myInputObject() As Process

#End Region

#Region "CmdletOverrides"
        ''' <summary>
        ''' For each of the requested processnames:
        ''' 1) check it's not a special process
        ''' 2) attempt to stop that process.
        ''' If no process requested, then nothing occurs.
        ''' </summary>
        Protected Overrides Sub ProcessRecord()
            Select Case ParameterSetName
                Case "ProcessName"
                    ProcessByName()

                Case "ProcessId"
                    ProcessById()

                Case "InputObject"
                    Dim process As Process
                    For Each process In myInputObject
                        SafeStopProcess(process)
                    Next process

                Case Else
                    Throw New ArgumentException("Bad ParameterSet Name")
            End Select

        End Sub 'ProcessRecord ' ProcessRecord
#End Region

#Region "Helper Methods"
        ''' <summary>
        ''' Returns all processes with matching names.
        ''' </summary>
        ''' <param name="processName">
        ''' The name of the process(es) to return
        ''' </param>
        ''' <param name="allProcesses">An array of all
        ''' machine processes.</param>
        ''' <returns>An array of matching processes.</returns>
        Friend Function SafeGetProcessesByName(ByVal processName As String, _
            ByRef allProcesses As ArrayList) As ArrayList

            ' Create and array to store the matching processes.
            Dim matchingProcesses As New ArrayList()

            ' Create the wildcard for pattern matching.
            Dim options As WildcardOptions = WildcardOptions.IgnoreCase Or _
                WildcardOptions.Compiled
            Dim wildcard As New WildcardPattern(processName, options)

            ' Walk all of the machine processes.
            Dim process As Process
            For Each process In allProcesses
                Dim processNameToMatch As String = Nothing
                Try
                    processNameToMatch = process.ProcessName
                Catch e As Win32Exception
                    ' Remove the process from the list so that it is not
                    ' checked again.
                    allProcesses.Remove(process)

                    Dim message As String = _
                        String.Format(CultureInfo.CurrentCulture, _
                            "The process ""{0}"" could not be found", processName)
                    WriteVerbose(message)
                    WriteError(New ErrorRecord(e, _
                        "ProcessNotFound", ErrorCategory.ObjectNotFound, _
                        processName))

                    GoTo ContinueForEach1
                End Try

                If Not wildcard.IsMatch(processNameToMatch) Then
                    GoTo ContinueForEach1
                End If

                matchingProcesses.Add(process)
ContinueForEach1:
            Next process
            Return matchingProcesses

        End Function 'SafeGetProcessesByName

        ''' <summary>
        ''' Safely stops a named process.  Used as standalone function
        ''' to declutter ProcessRecord method.
        ''' </summary>
        ''' <param name="process">The process to stop.</param>
        Private Sub SafeStopProcess(ByVal process As Process)
            Dim processName As String = Nothing

            Try
                processName = process.ProcessName
            Catch e As Win32Exception
                WriteError(New ErrorRecord(e, "ProcessNotFound", _
                    ErrorCategory.OpenError, processName))

                Return
            End Try

            ' Confirm the operation first.
            ' This is always false if WhatIf is set.
            If Not ShouldProcess(String.Format(CultureInfo.CurrentCulture, _
                    "{0} ({1})", processName, process.Id)) Then
                Return
            End If

            ' Make sure the user really wants to stop a critical
            ' process and possibly stop the machine.
            Dim criticalProcess As Boolean = _
                criticalProcessNames.Contains( _
                processName.ToLower(CultureInfo.CurrentCulture))

            Dim message As String = Nothing
            If criticalProcess AndAlso Not myForce Then
                message = String.Format(CultureInfo.CurrentCulture, _
                    "The process ""{0}"" is a critical process and " & _
                    "should not be stopped. " & _
                    "Are you sure you wish to stop the process?", processName)

                ' It is possible that ProcessRecord is called multiple
                ' when objects are recieved as inputs from a pipeline.
                ' So, to retain YesToAll and NoToAll input that the
                ' user may enter across mutilple calls to this
                ' function, they are stored as private members of the
                ' Cmdlet.
                If Not ShouldContinue(message, "Warning!", yesToAll, noToAll) Then
                    Return
                End If
            End If

            ' Display a warning information if stopping a critical
            ' process
            If criticalProcess Then
                message = String.Format(CultureInfo.CurrentCulture, _
                    "Stopping the critical process ""{0}"".", processName)
                WriteWarning(message)
            End If

            Try
                ' Stop the process.
                process.Kill()
            Catch e As Exception
                If TypeOf e Is Win32Exception OrElse TypeOf e Is SystemException _
                  OrElse TypeOf e Is InvalidOperationException Then
                    ' This process could not be stopped so write
                    ' a non-terminating error.
                    WriteError(New ErrorRecord(e, _
                        "CouldNotStopProcess", ErrorCategory.CloseError, process))
                    Return
                Else
                    Throw
                End If
            End Try

            ' Write a user-level message to the pipeline. These are
            ' intended to give the user detailed information on the
            ' operations performed by the Cmdlet. These messages will
            ' appear with the -Verbose option.
            message = String.Format(CultureInfo.CurrentCulture, _
                "Stopped process ""{0}"", pid {1}.", processName, process.Id)

            WriteVerbose(message)

            ' If the -PassThru command line argument is
            ' specified, pass the terminated process on.
            If myPassThru Then
                ' Write a debug message to the host which will be helpful
                ' in troubleshooting a problem. All debug messages
                ' will appear with the -Debug option
                message = String.Format(CultureInfo.CurrentCulture, _
                    "Writing process ""{0}"" to pipeline", processName)
                WriteDebug(message)
                WriteObject(process)
            End If

        End Sub 'SafeStopProcess


        ''' <summary>
        ''' Stop processes based on their names (using the
        ''' ParameterSetName as ProcessName)
        ''' </summary>
        Private Sub ProcessByName()
            Dim allProcesses As ArrayList = Nothing

            ' Get a list of all processes.
            Try
                allProcesses = New ArrayList(Process.GetProcesses())
            Catch ioe As InvalidOperationException
                MyBase.ThrowTerminatingError(New ErrorRecord(ioe, _
                    "UnableToAccessProcessList", _
                    ErrorCategory.InvalidOperation, Nothing))
            End Try

            ' If a name parameter is passed to cmdlet, get
            ' the associated process(es).
            ' Write a non-terminating error for failure to
            ' retrieve a process
            Dim name As String
            For Each name In processNames
                ' The allProcesses array list is passed as a reference because
                ' any process whose name cannot be obtained will be removed
                ' from the list so that its not compared the next time.
                Dim processes As ArrayList = SafeGetProcessesByName(name, _
                    allProcesses)

                ' If no processes were found write a non-terminating error.
                If processes.Count = 0 Then
                    WriteError(New ErrorRecord( _
                         New Exception("Process not found."), _
                         "ProcessNotFound", ErrorCategory.ObjectNotFound, name))
                Else
                    ' Otherwise terminate all processes in the list.
                    Dim process As Process
                    For Each process In processes
                        SafeStopProcess(process)
                    Next process
                End If

            Next name

        End Sub 'ProcessByName

        ''' <summary>
        ''' Stop processes based on their ids (using the
        ''' ParameterSetName as ProcessIds)
        ''' </summary>
        Friend Sub ProcessById()
            Dim processId As Integer
            For Each processId In processIds
                Dim process As Process = Nothing
                Try
                    process = System.Diagnostics.Process.GetProcessById(processId)

                    ' Write a debug message to the host which will be helpful
                    ' in troubleshooting a problem. All debug messages
                    ' will appear with the -Debug option
                    Dim message As String = String.Format( _
                        CultureInfo.CurrentCulture, _
                        "Acquired process for pid : {0}", process.Id)
                    WriteDebug(message)
                Catch ae As ArgumentException
                    Dim message As String = String.Format( _
                        CultureInfo.CurrentCulture, _
                        "The process id {0} could not be found", processId)
                    WriteVerbose(message)
                    WriteError(New ErrorRecord(ae, _
                        "ProcessIdNotFound", _
                         ErrorCategory.ObjectNotFound, processId))
                    GoTo ContinueForEach1
                End Try

                SafeStopProcess(process)
ContinueForEach1:
            Next processId

        End Sub 'ProcessById ' ProcessById
#End Region

#Region "Private Data"

        Private yesToAll, noToAll As Boolean

        ''' <summary>
        ''' Partial list of critical processes that should not be
        ''' stopped.  Lower case is used for case insensitive matching.
        ''' </summary>
        Private criticalProcessNames As New ArrayList( _
            New String() {"system", "winlogon", "spoolsv", "calc"})

#End Region

    End Class 'StopProcCommand

#End Region

#Region "PowerShell snap-in" '
    ''' <summary>
    ''' Create this sample as an PowerShell snap-in
    ''' </summary>
    <RunInstaller(True)> _
    Public Class StopProcPSSnapIn04
        Inherits PSSnapIn

        ''' <summary>
        ''' Create an instance of the StopProcPSSnapIn04
        ''' </summary>
        Public Sub New()

        End Sub 'New

        ''' <summary>
        ''' Get a name for this PowerShell snap-in. This name will
        ''' be used in registering this PowerShell snap-in.
        ''' </summary>
        Public Overrides ReadOnly Property Name() As String
            Get
                Return "StopProcPSSnapIn04"
            End Get
        End Property

        ''' <summary>
        ''' Vendor information for this PowerShell snap-in.
        ''' </summary>

        Public Overrides ReadOnly Property Vendor() As String
            Get
                Return "Microsoft"
            End Get
        End Property

        ''' <summary>
        ''' Gets resource information for vendor. This is a string of format:
        ''' resourceBaseName,resourceName.
        ''' </summary>
        Public Overrides ReadOnly Property VendorResource() As String
            Get
                Return "StopProcPSSnapIn04,Microsoft"
            End Get
        End Property

        ''' <summary>
        ''' Description of this PowerShell snap-in.
        ''' </summary>
        Public Overrides ReadOnly Property Description() As String
            Get
                Return "This is a PowerShell snap-in that includes " & _
                    "the stop-proc cmdlet."
            End Get
        End Property
    End Class 'StopProcPSSnapIn04

#End Region

End Namespace
```

<!-- TODO!!!: [!code-csharp[StopProcessSample04.vb](../../powershell-sdk-samples/SDK-2.0/vb/StopProcessSample04/StopProcessSample04.vb#L09-L456 "StopProcessSample04.vb")] -->

## <a name="see-also"></a><span data-ttu-id="dedc6-111">Véase también</span><span class="sxs-lookup"><span data-stu-id="dedc6-111">See Also</span></span>

[<span data-ttu-id="dedc6-112">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dedc6-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="dedc6-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="dedc6-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)