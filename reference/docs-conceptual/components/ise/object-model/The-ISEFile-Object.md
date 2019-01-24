---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: El objeto ISEFile
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 24549720b8bc35435882533b0eb138de432ede65
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403010"
---
# <a name="the-isefile-object"></a><span data-ttu-id="30484-103">El objeto ISEFile</span><span class="sxs-lookup"><span data-stu-id="30484-103">The ISEFile Object</span></span>

<span data-ttu-id="30484-104">Un objeto **ISEFile** representa un archivo en el Entorno de scripting integrado (ISE) de Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="30484-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="30484-105">Es una instancia de la clase Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="30484-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="30484-106">Este tema enumera sus métodos de miembro y propiedades de miembro.</span><span class="sxs-lookup"><span data-stu-id="30484-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="30484-107">**$psISE.CurrentFile** y los archivos de la colección de archivos en una pestaña de PowerShell son todas las instancias de la clase Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="30484-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="30484-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="30484-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="30484-109">Save\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="30484-109">Save\( \[saveEncoding\] \)</span></span>

<span data-ttu-id="30484-110">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="30484-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="30484-111">Guarda el archivo en disco.</span><span class="sxs-lookup"><span data-stu-id="30484-111">Saves the file to disk.</span></span>

<span data-ttu-id="30484-112">**\[saveEncoding\]**: [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) opcional. Un parámetro de codificación de carácter opcional que se usará para el archivo guardado.</span><span class="sxs-lookup"><span data-stu-id="30484-112">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="30484-113">El valor predeterminado es **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="30484-113">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="30484-114">Excepciones</span><span class="sxs-lookup"><span data-stu-id="30484-114">Exceptions</span></span>

- <span data-ttu-id="30484-115">**System.IO.IOException**: No se pudo guardar el archivo.</span><span class="sxs-lookup"><span data-stu-id="30484-115">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="30484-116">SaveAs\(nombre de archivo, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="30484-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>

<span data-ttu-id="30484-117">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="30484-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="30484-118">Guarda el archivo con el nombre de archivo y codificación especificados.</span><span class="sxs-lookup"><span data-stu-id="30484-118">Saves the file with the specified file name and encoding.</span></span>

<span data-ttu-id="30484-119">**filename**: cadena. El nombre que se utilizará para guardar el archivo.</span><span class="sxs-lookup"><span data-stu-id="30484-119">**filename** - String The name to be used to save the file.</span></span>

<span data-ttu-id="30484-120">**\[saveEncoding\]**: [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) opcional. Un parámetro de codificación de carácter opcional que se usará para el archivo guardado.</span><span class="sxs-lookup"><span data-stu-id="30484-120">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="30484-121">El valor predeterminado es **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="30484-121">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="30484-122">Excepciones</span><span class="sxs-lookup"><span data-stu-id="30484-122">Exceptions</span></span>

- <span data-ttu-id="30484-123">**System.ArgumentNullException**: El **filename** parámetro es null.</span><span class="sxs-lookup"><span data-stu-id="30484-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>
- <span data-ttu-id="30484-124">**System.ArgumentException**: El **filename** parámetro está vacío.</span><span class="sxs-lookup"><span data-stu-id="30484-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>
- <span data-ttu-id="30484-125">**System.IO.IOException**: No se pudo guardar el archivo.</span><span class="sxs-lookup"><span data-stu-id="30484-125">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a><span data-ttu-id="30484-126">Propiedades</span><span class="sxs-lookup"><span data-stu-id="30484-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="30484-127">DisplayName</span><span class="sxs-lookup"><span data-stu-id="30484-127">DisplayName</span></span>

<span data-ttu-id="30484-128">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="30484-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="30484-129">La propiedad de solo lectura que obtiene la cadena que contiene el nombre para mostrar de este archivo.</span><span class="sxs-lookup"><span data-stu-id="30484-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="30484-130">El nombre se muestra en la pestaña **Archivo** en la parte superior del editor.</span><span class="sxs-lookup"><span data-stu-id="30484-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="30484-131">La presencia de un asterisco \(\*\) al final del nombre indica que el archivo tiene cambios que no se han guardado.</span><span class="sxs-lookup"><span data-stu-id="30484-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a><span data-ttu-id="30484-132">Editor</span><span class="sxs-lookup"><span data-stu-id="30484-132">Editor</span></span>

<span data-ttu-id="30484-133">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="30484-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="30484-134">La propiedad de solo lectura que obtiene el [objeto de editor](The-ISEEditor-Object.md) que se utiliza para el archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="30484-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a><span data-ttu-id="30484-135">Codificación</span><span class="sxs-lookup"><span data-stu-id="30484-135">Encoding</span></span>

<span data-ttu-id="30484-136">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="30484-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="30484-137">La propiedad de solo lectura que obtiene la codificación del archivo original.</span><span class="sxs-lookup"><span data-stu-id="30484-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="30484-138">Se trata de un objeto **System.Text.Encoding**.</span><span class="sxs-lookup"><span data-stu-id="30484-138">This is a **System.Text.Encoding** object.</span></span>

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a><span data-ttu-id="30484-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="30484-139">FullPath</span></span>

<span data-ttu-id="30484-140">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="30484-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="30484-141">La propiedad de solo lectura que obtiene la cadena que especifica la ruta de acceso completa del archivo abierto.</span><span class="sxs-lookup"><span data-stu-id="30484-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a><span data-ttu-id="30484-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="30484-142">IsSaved</span></span>

<span data-ttu-id="30484-143">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="30484-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="30484-144">La propiedad booleana de solo lectura que devuelve **$true** si el archivo se ha guardado una vez que se modificó por última vez.</span><span class="sxs-lookup"><span data-stu-id="30484-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a><span data-ttu-id="30484-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="30484-145">IsUntitled</span></span>

<span data-ttu-id="30484-146">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="30484-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="30484-147">La propiedad de solo lectura que devuelve **$true** si nunca se asignó un título al archivo.</span><span class="sxs-lookup"><span data-stu-id="30484-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a><span data-ttu-id="30484-148">Véase también</span><span class="sxs-lookup"><span data-stu-id="30484-148">See Also</span></span>

- [<span data-ttu-id="30484-149">ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="30484-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md)
- [<span data-ttu-id="30484-150">Finalidad del modelo de objetos de scripting de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="30484-150">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="30484-151">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="30484-151">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)