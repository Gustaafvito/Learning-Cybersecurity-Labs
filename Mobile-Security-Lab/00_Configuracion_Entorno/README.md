# 🛠️ Configuración del Entorno de Hacking Android (ADB & Fastboot)

Este documento detalla el proceso de instalación de las **Android SDK Platform Tools** en Windows. Estas herramientas son necesarias para interactuar con los dispositivos (instalar apps, extraer logs, flashear ROMs, etc.).

## 1. Descarga de Herramientas
No utilizamos instaladores `.exe` de terceros. Usamos los binarios oficiales de Google para máxima seguridad.

* **Fuente Oficial:** [Android Developers - SDK Platform Tools](https://developer.android.com/tools/releases/platform-tools)
* **Archivo descargado:** `platform-tools_rXX.X.X-windows.zip`

## 2. Instalación "Manual" (Recomendada)
Para mantener el sistema limpio y portable, realizamos una instalación manual en la raíz del disco.

### Pasos realizados:
1.  Descomprimir el archivo ZIP descargado.
2.  Renombrar la carpeta resultante a `adb`.
3.  Mover la carpeta a la raíz del disco local para tener una ruta corta y sin espacios.
    * **Ruta final:** `C:\adb\`

## 3. Verificación de la Instalación
Abrimos una terminal (PowerShell o CMD) y navegamos a la ruta de instalación para verificar que el binario funciona.

```powershell
cd C:\adb
.\adb version
