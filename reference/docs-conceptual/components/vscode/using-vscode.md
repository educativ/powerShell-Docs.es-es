---
title: Uso de Visual Studio Code para el desarrollo de PowerShell
description: Uso de Visual Studio Code para el desarrollo de PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 0e082b74f99d214749f10224fb5aaf41e2ef8951
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71325243"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Uso de Visual Studio Code para el desarrollo de PowerShell

Además de [PowerShell ISE][ise], PowerShell también se admite en Visual Studio Code (VSCode). Por otra parte, el ISE no es compatible con PowerShell Core, mientras que VSCode es compatible con PowerShell Core en todas las plataformas (Windows, macOS y Linux).

Puede usar VSCode en Windows con PowerShell versión 5 a través de Windows 10 o mediante la instalación de [Windows Management Framework 5.0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/) para sistemas operativos Windows inferiores (por ejemplo, Windows 8.1, etc).

Antes de iniciarlo, asegúrese de que tiene PowerShell en el sistema. Para cargas de trabajo modernas de Windows, macOS y Linux, vea:

- [Instalación de PowerShell Core en Linux][install-pscore-linux]
- [Instalación de PowerShell Core en macOS][install-pscore-macos]
- [Instalación de PowerShell Core en Windows][install-pscore-windows]

Para las cargas de trabajo de Windows PowerShell tradicionales, vea [Instalación de Windows PowerShell][install-winps].

## <a name="editing-with-vscode"></a>Edición con VSCode

1. [Instalación de VSCode](https://code.visualstudio.com/Docs/setup/setup-overview)

   - **Linux**: siga las instrucciones de instalación de la página [Ejecución de VSCode en Linux](https://code.visualstudio.com/docs/setup/linux).
   - **macOS**: siga las instrucciones de instalación de la página [Ejecución de VSCode en macOS](https://code.visualstudio.com/docs/setup/mac).

     > [!IMPORTANT]
     > En macOS, debe instalar OpenSSL para que la extensión de PowerShell funcione correctamente. La manera más fácil de hacerlo consiste en instalar [Homebrew](https://brew.sh/) y ejecutar `brew install openssl`. Ahora VSCode puede cargar la extensión de PowerShell correctamente.

   - **Windows**: siga las instrucciones de instalación de la página [Ejecución de VSCode en Windows](https://code.visualstudio.com/docs/setup/windows).

2. Instalación de la extensión de PowerShell

   - Inicie la aplicación VSCode de la siguiente manera:
     - **Windows**: escriba `code` en la sesión de PowerShell.
     - **Linux**: escriba `code` en el terminal.
     - **macOS**: escriba `code` en el terminal.
   - Inicie **Quick Open**. Para ello, presione <kbd>CTRL</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>P</kbd> en Mac).
   - En Quick Open, escriba `ext install powershell` y presione **ENTRAR**.
   - Se abre la vista **Extensiones** en la barra lateral. Seleccione la extensión de PowerShell de Microsoft.
     Debería ver algo parecido a lo siguiente:

     ![VSCode](../../images/using-vscode/vscode.png)

   - Haga clic en el botón **Instalar** en la extensión de PowerShell de Microsoft.
   - Después de la instalación, se ve que el botón **Instalar** cambia a **Recargar**. Haga clic en **Recargar**.
   - Una vez que se haya vuelto a cargar VSCode, estará listo para la edición.

Por ejemplo, para crear un archivo, haga clic en **Archivo -> Nuevo**. Para guardarlo, haga clic en **Archivo -> Guardar** y proporcione un nombre de archivo; por ejemplo, `HelloWorld.ps1`. Para cerrar el archivo, haga clic en "x" junto al nombre de archivo. Para salir de VSCode, **Archivo->Salir**.

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>Instalación de la extensión de PowerShell en sistemas restringidos

Algunos sistemas se configuran de una manera que requiere que todas las firmas de código se verifiquen y, por lo tanto, requiere que los servicios del editor de PowerShell se aprueben manualmente para ejecutarse en el sistema. Una actualización de la directiva de grupo que cambie la directiva de ejecución es una causa probable de recibir un error como este si ha instalado la extensión de PowerShell:

```
Language server startup failed.
```

Para aprobar manualmente los servicios del Editor de PowerShell y, por tanto, la extensión de PowerShell para VSCode, abra un símbolo del sistema y ejecute:

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

Se le preguntará si desea ejecutar software de este publicador que no es de confianza. Escriba `R` para ejecutar el archivo. A continuación, abra VSCode y compruebe que la extensión de PowerShell funciona correctamente. Si sigue teniendo problemas para comenzar, háganoslo saber en [GitHub](https://github.com/PowerShell/vscode-powershell/issues).

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>Elección de una versión de PowerShell para usarla con la extensión

Con la instalación de PowerShell Core en paralelo con Windows PowerShell, ahora es posible usar una versión determinada de PowerShell con la extensión de PowerShell. Siga estas etapas para escolher a versão:

1. Abra la paleta de comandos (<kbd>Ctrl</kbd>+<kbd>Mayús</kbd>+<kbd>P</kbd> en Windows y Linux, <kbd>Cmd</kbd>+<kbd>Mayús</kbd>+<kbd>P</kbd> en macOS).
1. Busque "Sesión".
1. Haga clic en "PowerShell: Show Session Menu" (PowerShell: Mostrar menú de sesión).
1. Elija en la lista la versión de PowerShell que quiere usar, por ejemplo, "PowerShell Core".

> [!IMPORTANT]
> Esta característica examina algunas rutas de acceso conocidas en distintos sistemas operativos para detectar las ubicaciones de instalación de PowerShell. O PowerShell pode não ser inicialmente mostrado no menu de sessão caso você o tenha instalado em um local atípico. Para extender el menú de la sesión, [agregue sus propias rutas de acceso personalizadas](#adding-your-own-powershell-paths-to-the-session-menu) tal como se describe a continuación.

>[!NOTE]
> Esta es otra forma de acceder al menú de la sesión. Cuando se abre un archivo de PowerShell en el editor, verá un número de versión verde en la esquina inferior derecha. Haga clic en este número de versión para acceder al menú de la sesión.

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>Adición de rutas de acceso propias de PowerShell al menú de sesión

Puede agregar otras rutas de acceso ejecutables de PowerShell al menú de sesión mediante una configuración de VSCode.

Agregue un elemento a la lista `powershell.powerShellAdditionalExePaths` o cree la lista si no existe en su `settings.json`:

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    // other settings...
}
```

Cada elemento debe tener:

* `exePath`: la ruta de acceso al ejecutable `pwsh` o `powershell`.
* `versionName`: el texto que se mostrará en el menú de la sesión.

Puede establecer la versión de PowerShell que desea usar. Para ello, use el valor `powershell.powerShellDefaultVersion` configurándolo al texto que se muestra en el menú de sesión (también conocido como `versionName` en la última configuración).

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",

    // other settings...
}
```

A continuación, reinicie VSCode o use la paleta de comandos "Desarrollador: Recargar ventana" para volver a cargar la ventana actual de VSCode.

Si abre el menú de la sesión, ahora verá las versiones adicionales de PowerShell.

> [!NOTE]
> Si compila PowerShell a partir del código fuente, se trata de una excelente forma de probar la compilación local de PowerShell.

#### <a name="configuration-settings-for-vscode"></a>Valores de configuración de VSCode

Mediante los pasos del párrafo anterior, puede agregar valores de configuración en `settings.json`.

Recomendamos los valores de configuración siguientes para VSCode:

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Si no desea que estos ajustes afecten a todos los tipos de archivos, VSCode también permite configuraciones por idioma. Cree un ajuste específico del lenguaje colocando los ajustes en un campo `[<language-name>]`. Por ejemplo:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Para obtener más información sobre la codificación de archivo en VSCode, vea [Descripción de la codificación de archivo](understanding-file-encoding.md).

## <a name="debugging-with-vscode"></a>Depuración con VSCode

### <a name="no-workspace-debugging"></a>Depuración fuera del área de trabajo

A partir de VSCode versión 1.9 puede depurar scripts de PowerShell sin tener que abrir la carpeta que contiene el script de PowerShell. Abra el archivo de script de PowerShell con **Archivo -> Abrir archivo…** , establezca un punto de interrupción en una línea (presione <kbd>F9</kbd>) y, después, presione <kbd>F5</kbd> para iniciar la depuración. Aparece el panel de acciones de depuración, que le permite obtener acceso al depurador, realizar la depuración paso a paso, reanudarla y detenerla.

### <a name="workspace-debugging"></a>Depuración del área de trabajo

La depuración del área de trabajo hace referencia a la depuración en el contexto de una carpeta que se ha abierto en Visual Studio Code mediante **Abrir carpeta…** desde el menú **Archivo**. Suele tratarse de la carpeta del proyecto de PowerShell o la raíz del repositorio de Git.

Incluso en este modo, para empezar a depurar el script de PowerShell seleccionado, basta con presionar <kbd>F5</kbd>. La depuración del área de trabajo no se limita a depurar el archivo abierto actualmente, sino que permite definir diversas configuraciones de depuración. Por ejemplo, puede agregar configuraciones para:

- Iniciar pruebas de Pester en el depurador
- Iniciar un archivo específico con argumentos en el depurador
- Iniciar una sesión interactiva en el depurador
- Asociar el depurador a un proceso de host de PowerShell

Siga los pasos siguientes para crear el archivo de configuración de depuración:

  1. Abra la vista **Depurar**. Para ello, presione <kbd>Ctrl</kbd>+<kbd>Mayús</kbd>+<kbd>D</kbd> (<kbd>Cmd</kbd>+<kbd>Mayús</kbd>+<kbd>D</kbd> en Mac).
  2. Haga clic en el icono de engranaje **Configurar** en la barra de herramientas.
  3. VSCode le solicita que **seleccione un entorno**. Elija **PowerShell**.

  Cuando lo haga, VSCode creará un directorio y un archivo ".vscode\launch.json" en la raíz de la carpeta del área de trabajo. Aquí es donde se almacenará la configuración de depuración. Si los archivos están en un repositorio de Git, normalmente le interesa confirmar el archivo launch.json. El contenido del archivo launch.json es el siguiente:

  ```json
  {
    "version": "0.2.0",
    "configurations": [
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Launch (current file)",
            "script": "${file}",
            "args": [],
            "cwd": "${file}"
        },
        {
            "type": "PowerShell",
            "request": "attach",
            "name": "PowerShell Attach to Host Process",
            "processId": "${command.PickPSHostProcess}",
            "runspaceId": 1
        },
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Interactive Session",
            "cwd": "${workspaceRoot}"
        }
    ]
  }
  ```

  Esto representa los escenarios de depuración comunes. Aun así, cuando se abre este archivo en el editor, se ve el botón **Agregar configuración…** . Puede hacer clic en este botón para agregar más configuraciones de depuración de PowerShell. Una configuración muy útil que conviene agregar es **PowerShell: Iniciar Script**. Con esta configuración, puede especificar un archivo concreto con argumentos opcionales que se debe iniciar cada vez que se presione <kbd>F5</kbd>, independientemente del archivo que esté activo en el momento en el editor.

  Una vez establecida la configuración de depuración, puede seleccionar la configuración que quiere usar durante una sesión de depuración. Para ello, selecciónela en el menú desplegable de la barra de herramientas de la vista **Depurar**.

Algunos blogs pueden servirle de ayuda para empezar a usar la extensión de PowerShell para Visual Studio Code:

- [Extensión de PowerShell][ps-extension]
- [Escritura y depuración de scripts de PowerShell en Visual Studio Code][debug]
- [Instrucciones de depuración de Visual Studio Code][vscode-guide]
- [Depuración de PowerShell en Visual Studio Code][ps-vscode]
- [Introducción al desarrollo de PowerShell en Visual Studio Code][getting-started]
- [Características de edición de Visual Studio Code para el desarrollo de PowerShell, parte 1][editing-part1]
- [Características de edición de Visual Studio Code para el desarrollo de PowerShell, parte 2][editing-part2]
- [Depuración de scripts de PowerShell en Visual Studio Code, parte 1][debugging-part1]
- [Depuración de scripts de PowerShell en Visual Studio Code, parte 2][debugging-part2]

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-vscode"></a>Extensión de PowerShell para VSCode

Encontrará en [GitHub](https://github.com/PowerShell/vscode-powershell) el código fuente de la extensión de PowerShell.
