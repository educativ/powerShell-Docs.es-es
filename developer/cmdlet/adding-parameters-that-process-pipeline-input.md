---
title: Adición de parámetros que procesan la entrada de la canalización | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: c790d20a792bcdb4a34485e53375560e129433a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854541"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="a3036-102">Adición de parámetros que procesan la entrada de la canalización</span><span class="sxs-lookup"><span data-stu-id="a3036-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="a3036-103">Un origen de entrada para un cmdlet es un objeto en la canalización que se origina en un cmdlet de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="a3036-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="a3036-104">En esta sección se describe cómo agregar un parámetro al cmdlet Get-Proc (se describe en [crear su primer Cmdlet](./creating-a-cmdlet-without-parameters.md)) para que el cmdlet puede procesar objetos de la canalización.</span><span class="sxs-lookup"><span data-stu-id="a3036-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="a3036-105">Este cmdlet Get-Proc usa un `Name` parámetro que acepta la entrada desde un objeto de canalización, recupera información de proceso del equipo local en función de los nombres proporcionados y, a continuación, muestra información acerca de los procesos en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="a3036-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

<span data-ttu-id="a3036-106">Temas de esta sección incluyen lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a3036-106">Topics in this section include the following:</span></span>

- [<span data-ttu-id="a3036-107">Definición de la clase de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a3036-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="a3036-108">Definir la entrada de la canalización</span><span class="sxs-lookup"><span data-stu-id="a3036-108">Defining Input from the Pipeline</span></span>](#Defining-Input-from-the-Pipeline)

- [<span data-ttu-id="a3036-109">Reemplazar una método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="a3036-109">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="a3036-110">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="a3036-110">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="a3036-111">Definir los tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="a3036-111">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="a3036-112">Compilar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a3036-112">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="a3036-113">Probar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a3036-113">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="a3036-114">Definición de la clase de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a3036-114">Defining the Cmdlet Class</span></span>

<span data-ttu-id="a3036-115">El primer paso en la creación de cmdlet siempre es el cmdlet de nomenclatura y declarar la clase de .NET que implementa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3036-115">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="a3036-116">Este cmdlet recupera información de proceso, por lo que el nombre del verbo seleccionado aquí es "Get".</span><span class="sxs-lookup"><span data-stu-id="a3036-116">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="a3036-117">(Casi cualquier tipo de cmdlet que es capaz de recuperar la información puede procesar la entrada de línea de comandos). Para obtener más información acerca de los verbos de cmdlet aprobadas, consulte [los nombres de verbo del Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="a3036-117">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="a3036-118">La siguiente es la definición de este cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="a3036-118">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="a3036-119">Se proporcionan detalles de esta definición [crear su primer Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a3036-119">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="a3036-120">Definir la entrada de la canalización</span><span class="sxs-lookup"><span data-stu-id="a3036-120">Defining Input from the Pipeline</span></span>

<span data-ttu-id="a3036-121">En esta sección se describe cómo definir la entrada de la canalización para un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3036-121">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="a3036-122">Este cmdlet Get-Proc define una propiedad que representa el `Name` parámetro tal y como se describe en [agregar parámetros que procesan datos de línea de comandos](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="a3036-122">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span> <span data-ttu-id="a3036-123">(Consulte ese tema para obtener información general sobre la declaración de parámetros).</span><span class="sxs-lookup"><span data-stu-id="a3036-123">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="a3036-124">Sin embargo, cuando un cmdlet debe procesar la entrada de la canalización, debe tener sus parámetros enlazados a los valores de entrada por el tiempo de ejecución de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3036-124">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="a3036-125">Para ello, debe agregar el `ValueFromPipeline` palabra clave o agregar el `ValueFromPipelineByProperty` palabra clave para el [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaración de atributos.</span><span class="sxs-lookup"><span data-stu-id="a3036-125">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="a3036-126">Especifique el `ValueFromPipeline` palabra clave si el cmdlet obtiene acceso al objeto de entrada completando.</span><span class="sxs-lookup"><span data-stu-id="a3036-126">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="a3036-127">Especifique el `ValueFromPipelineByProperty` si el cmdlet obtiene acceso a una propiedad del objeto.</span><span class="sxs-lookup"><span data-stu-id="a3036-127">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="a3036-128">Esta es la declaración de parámetros para el `Name` parámetro de este cmdlet Get-Proc que acepta la entrada de la canalización.</span><span class="sxs-lookup"><span data-stu-id="a3036-128">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

<span data-ttu-id="a3036-129">Los conjuntos de la declaración anterior el `ValueFromPipeline` palabra clave para `true` para que el tiempo de ejecución de Windows PowerShell enlazará el parámetro para el objeto entrante, si el objeto es el mismo tipo que el parámetro, o si se puede convertirse en el mismo tipo.</span><span class="sxs-lookup"><span data-stu-id="a3036-129">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="a3036-130">El `ValueFromPipelineByPropertyName` palabra clave también se establece en `true` para que el tiempo de ejecución de Windows PowerShell comprobará el objeto entrante para un `Name` propiedad.</span><span class="sxs-lookup"><span data-stu-id="a3036-130">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="a3036-131">Si el objeto entrante tiene dicha propiedad, el tiempo de ejecución se enlazará el `Name` parámetro para el `Name` propiedad del objeto entrante.</span><span class="sxs-lookup"><span data-stu-id="a3036-131">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="a3036-132">La configuración de la `ValueFromPipeline` palabra clave de atributo de un parámetro tiene prioridad sobre la configuración de la `ValueFromPipelineByPropertyName` palabra clave.</span><span class="sxs-lookup"><span data-stu-id="a3036-132">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="a3036-133">Reemplazar una método de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="a3036-133">Overriding an Input Processing Method</span></span>

<span data-ttu-id="a3036-134">Si es su cmdlet controlar la entrada de canalización, debe invalidar los métodos de procesamiento de entrada adecuada.</span><span class="sxs-lookup"><span data-stu-id="a3036-134">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="a3036-135">Los métodos de procesamiento de entrada básico se introducen en [crear su primer Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a3036-135">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="a3036-136">Este cmdlet Get-Proc invalida la [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para controlar el `Name` proporcionado por el usuario o un script de entrada de parámetros.</span><span class="sxs-lookup"><span data-stu-id="a3036-136">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="a3036-137">Este método obtiene los procesos para cada nombre de proceso solicitado o todos los procesos si se proporciona ningún nombre.</span><span class="sxs-lookup"><span data-stu-id="a3036-137">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="a3036-138">Tenga en cuenta que dentro de [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), la llamada a [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) es el mecanismo de salida para enviar objetos de salida a la canalización.</span><span class="sxs-lookup"><span data-stu-id="a3036-138">Notice that within [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="a3036-139">El segundo parámetro de esta llamada, `enumerateCollection`, se establece en `true` para indicar al runtime de Windows PowerShell para enumerar la matriz de objetos de proceso y escribir un proceso a la vez en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="a3036-139">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument of this call tells
      // PowerShell to enumerate the array, and send one process at a
      // time to the pipeline.
      WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="a3036-140">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="a3036-140">Code Sample</span></span>

<span data-ttu-id="a3036-141">Para la completa C# código de ejemplo, vea [GetProcessSample03 ejemplo](./getprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a3036-141">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="a3036-142">Definir los tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="a3036-142">Defining Object Types and Formatting</span></span>

<span data-ttu-id="a3036-143">Windows PowerShell pasa información entre cmdlets mediante objetos. NET.</span><span class="sxs-lookup"><span data-stu-id="a3036-143">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="a3036-144">Por lo tanto, un cmdlet que deba definir su propio tipo o el cmdlet puede necesitar extender un tipo existente proporcionado por otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3036-144">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="a3036-145">Para obtener más información acerca de los nuevos tipos se definen o amplían los tipos existentes, consulte [extender los tipos de objeto y formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="a3036-145">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="a3036-146">Compilar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a3036-146">Building the Cmdlet</span></span>

<span data-ttu-id="a3036-147">Después de implementar un cmdlet se debe registrar con Windows PowerShell a través de un complemento de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3036-147">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="a3036-148">Para obtener más información sobre cómo registrar cmdlets, consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="a3036-148">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="a3036-149">Probar el Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a3036-149">Testing the Cmdlet</span></span>

<span data-ttu-id="a3036-150">Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarla mediante la ejecución de la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="a3036-150">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="a3036-151">Por ejemplo, pruebe el código para el cmdlet de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="a3036-151">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="a3036-152">Para obtener más información sobre el uso de cmdlets de la línea de comandos, consulte el [Introducción a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="a3036-152">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="a3036-153">En el símbolo del sistema de Windows PowerShell, escriba los comandos siguientes para recuperar los nombres de proceso a través de la canalización.</span><span class="sxs-lookup"><span data-stu-id="a3036-153">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

    ```powershell
    PS> type ProcessNames | get-proc
    ```

<span data-ttu-id="a3036-154">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="a3036-154">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- <span data-ttu-id="a3036-155">Escriba las líneas siguientes para obtener los objetos de proceso que tienen un `Name` propiedad de los procesos denominados "IEXPLORE".</span><span class="sxs-lookup"><span data-stu-id="a3036-155">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="a3036-156">Este ejemplo se usa el `Get-Process` cmdlet (proporcionado por Windows PowerShell) como un comando para recuperar los procesos "IEXPLORE" ascendente.</span><span class="sxs-lookup"><span data-stu-id="a3036-156">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

    ```powershell
    PS> get-process iexplore | get-proc
    ```

<span data-ttu-id="a3036-157">Aparece el siguiente resultado.</span><span class="sxs-lookup"><span data-stu-id="a3036-157">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a><span data-ttu-id="a3036-158">Véase también</span><span class="sxs-lookup"><span data-stu-id="a3036-158">See Also</span></span>

[<span data-ttu-id="a3036-159">Adición de parámetros que procesa la entrada de línea de comandos</span><span class="sxs-lookup"><span data-stu-id="a3036-159">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="a3036-160">Creación del primer Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a3036-160">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="a3036-161">Extensión de tipos de objeto y el formato</span><span class="sxs-lookup"><span data-stu-id="a3036-161">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="a3036-162">Cómo registrar Cmdlets, proveedores y aplicaciones Host</span><span class="sxs-lookup"><span data-stu-id="a3036-162">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="a3036-163">Referencia de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a3036-163">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="a3036-164">Ejemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="a3036-164">Cmdlet Samples</span></span>](./cmdlet-samples.md)