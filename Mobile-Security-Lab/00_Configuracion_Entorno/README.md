# 🛠️ Configuración del Entorno: ADB y Fastboot

Guía de instalación de las herramientas **Android Debug Bridge (ADB)** en Windows. Este es el paso previo necesario antes de conectar cualquier móvil.

## 📋 Requisitos
* PC con Windows.
* Descarga oficial: [SDK Platform-Tools](https://developer.android.com/tools/releases/platform-tools)

---

## 🚀 1. Instalación Manual

1.  Crear una carpeta llamada `adb` en la raíz del disco local `C:\`.
2.  Descomprimir el contenido del ZIP descargado dentro de esa carpeta.

**Resultado Correcto:**
La ruta debe ser `C:\adb\` y contener los ejecutables `adb.exe` y `fastboot.exe`:

![Archivos ADB](img/01_archivos_adb_raiz.png)

---

## ✅ 2. Verificación del Sistema

Para confirmar que la herramienta funciona, abrimos una terminal y consultamos la versión.

1.  Abrir PowerShell en la carpeta `C:\adb`.
2.  Ejecutar el comando: `.\adb version`

**Resultado Correcto:**
El sistema devuelve la versión instalada, confirmando que ADB está listo para usarse:

![Versión Terminal](img/02_verificacion_terminal.png)

---

## ⏭️ Siguientes Pasos
Ahora que el entorno está configurado, el siguiente paso es ir a la carpeta específica del dispositivo (ej: `/POCO_M5`) para realizar la conexión y extracción de datos.
