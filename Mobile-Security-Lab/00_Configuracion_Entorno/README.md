# 🛠️ Configuración del Entorno de Trabajo: ADB y Fastboot

Este documento detalla el procedimiento estándar para instalar las herramientas **Android Debug Bridge (ADB)** y **Fastboot** en un entorno Windows. Estas herramientas son indispensables para la comunicación a bajo nivel con dispositivos Android (instalación de APKs, extracción de logs, desbloqueo de bootloader, etc.).

## 📋 Requisitos Previos

* Un PC con Windows.
* Acceso a internet para descargar los binarios oficiales.

---

## 🚀 Proceso de Instalación

A diferencia de software convencional, ADB no utiliza un instalador `.exe`. Se trata de herramientas portables que deben ubicarse manualmente en el sistema.

### 1. Descarga de Binarios Oficiales

Utilizamos exclusivamente las **SDK Platform-Tools** proporcionadas por Google para garantizar la seguridad y estabilidad.

* **Enlace de descarga:** [Android Developers - SDK Platform-Tools](https://developer.android.com/tools/releases/platform-tools)
* **Archivo:** Descargar la versión correspondiente a Windows (archivo `.zip`).

### 2. Despliegue de Archivos

Para asegurar un funcionamiento correcto y una ruta de acceso sencilla en la terminal, se recomienda instalar las herramientas en la raíz del disco del sistema.

**Pasos:**
1.  Crear una carpeta llamada `adb` en la raíz del disco local `C:\`. Ruta final: `C:\adb\`.
2.  Extraer el contenido del archivo `.zip` descargado directamente en el interior de esta carpeta.

**Resultado esperado:**
La carpeta debe contener los ejecutables `adb.exe`, `fastboot.exe` y las librerías DLL necesarias, como se muestra en la siguiente imagen:

![Archivos ADB en la raíz](imagenes/01_archivos_adb_raiz.png)
*Figura 1: Estructura de archivos correcta en C:\adb\*

---

## ✅ Verificación de la Instalación

Para confirmar que el sistema puede ejecutar las herramientas correctamente, realizaremos una prueba desde la terminal.

**Pasos:**
1.  Navegar a la carpeta de instalación (`C:\adb`).
2.  Abrir una terminal (PowerShell o CMD) en esta ubicación.
    * *Tip: Shift + Clic Derecho en un espacio vacío -> "Abrir ventana de PowerShell aquí".*
3.  Ejecutar el comando de versión:

```powershell
# Si usas PowerShell:
.\adb version

# Si usas CMD:
adb version
