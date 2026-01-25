# 📱 Samsung Galaxy A71 (SM-A715F) - Auditoría y Conexión

Documentación técnica del proceso de conexión y configuración del dispositivo para el laboratorio de seguridad móvil.

## 🛠️ 1. Preparación del Entorno (Modo Desarrollador)

El primer paso crítico es habilitar el puente de depuración (ADB) oculto por defecto en Android 13 (One UI 5.1).

### Habilitar opciones de desarrollo
Navegamos a **Ajustes > Información de software** y pulsamos 7 veces sobre el número de compilación.

> **Evidencia:**
> ![Numero de Compilacion](img/numero_compilacion.png)

### Activar Depuración USB
Una vez habilitado el menú secreto, accedemos a **Opciones de desarrollador** y activamos el interruptor de depuración.

> **Evidencia:**
> ![Opciones de Desarrollador](img/opciones_desarrollador.png)

## 💻 2. Conexión Exitosa con Scrcpy

Tras conectar el cable USB y aceptar la huella RSA en el dispositivo, establecemos la conexión.

**Comando ejecutado:**
```bash
scrcpy
```

### 🔓 3. Desbloqueo de Bootloader (El paso crítico)

Tras verificar la conexión, confirmamos que la opción **Desbloqueo de OEM** está disponible y la activamos.

> **⚠️ AVISO:** Al activar este interruptor y proceder con el desbloqueo físico, la seguridad KNOX se romperá (0x1) y la garantía se anulará.

> **Evidencia:**
> ![Desbloqueo OEM Activado](img/desbloqueo_oem_activado.png)

---
**Estado actual:** Listo para `Download Mode` y flasheo de Recovery.

### 🔓 4. Confirmación Física del Desbloqueo

El dispositivo entra en modo de descarga y solicita confirmación física.

> **Paso 1: Confirmación**
> Pulsamos **Volumen Arriba** (Long Press) para entrar en modo Unlock y luego un toque corto para confirmar.
> ![Confirmacion Unlock](img/confirmacion_unlock.jpg)

> **Paso 2: Resultado**
> Al reiniciar, el sistema muestra la advertencia de seguridad que confirma el estado **UNLOCKED**.
> ![Aviso Bootloader](img/aviso_bootloader_unlocked.jpg)

---
**✅ ESTADO FINAL:** Bootloader abierto. KNOX 0x1. Listo para flashear Custom Recovery.

## ⚙️ 4. Preparación del Paquete de Recuperación

Samsung Odin requiere que las imágenes de partición (`.img`) estén encapsuladas en un archivo `.tar` para su flasheo a través del slot AP.

**Archivos procesados:**
* `recovery.img` (Lineage Recovery)
* `vbmeta.img` (Verified Boot Metadata)

**Acción realizada:**
Empaquetado mediante 7-Zip en formato TAR.
> **Resultado:** `lineage_recovery.tar` listo para inyección.

# 🛡️ Proyecto: La Joya de la Privacidad (Samsung Galaxy A71)

> **Dispositivo:** Samsung Galaxy A71 (SM-A715F)
> **Codename:** `a71`
> **Estado:** 🟢 COMPLETADO
> **OS Final:** LineageOS 23 (Android 16)
> **Fecha:** Enero 2026

---

## 🎯 Misión
Rescatar un dispositivo de la obsolescencia programada y del rastreo comercial (Samsung/Google), convirtiéndolo en un terminal seguro, privado y actualizado a la última versión de Android disponible.

## 🛠️ Herramientas
* **Hardware:** PC Windows 11, Cable USB-C Original.
* **Software Samsung:** Odin v3.14.4.
* **Herramientas ADB:** Google Platform Tools + `scrcpy`.
* **Gestión de Archivos:** 7-Zip (Creación de paquetes `.tar`).

---

## 📸 Bitácora de Ejecución

### FASE 1: Preparación del Entorno
Habilitación del modo desarrollador y depuración USB para preparar el terreno.
* **Build:** `numero_compilacion.png`
* **Menú:** `opciones_desarrollador.png`

![Build Info](img/numero_compilacion.png)

### FASE 2: Liberación del Bootloader
Superamos la seguridad "KG State: Prenormal" y procedemos al desbloqueo físico.

1.  **Habilitar OEM:** Interruptor crítico activado en ajustes.
    ![OEM Unlock](img/desbloqueo_oem_activado.png)

2.  **Confirmación Física:** Entramos en modo Unlock (Vol+ Largo) y confirmamos la rotura de garantía.
    ![Unlock Prompt](img/confirmacion_unlock.jpg)

3.  **Estado Unlocked:** La advertencia de seguridad confirma que el cerrojo digital está abierto.
    ![Warning](img/aviso_bootloader_unlocked.jpg)

### FASE 3: Inyección del Recovery
Sustitución del recovery de fábrica por el de LineageOS. Se requirió empaquetar `recovery.img` + `vbmeta.img` en un archivo `.tar` para Odin.

* **Configuración Crítica:** `Auto Reboot` **DESACTIVADO** en Odin.
    ![Odin Setup](img/4_odin_config.png)

* **Ejecución (Modo Download):**
    ![Download Mode](img/5_download_mode.jpg)

* **Resultado:** Inyección exitosa (PASS).
    ![Odin Pass](img/6_odin_pass.png)

### FASE 4: Instalación del Sistema (Sideload)
Accedimos al nuevo recovery, formateamos las particiones (`Format Data`) e instalamos el sistema operativo mediante carga lateral ADB.

1.  **Lineage Recovery:**
    ![Recovery Menu](img/7_recovery_menu.jpg)

2.  **Proceso de Instalación:**
    * **PC (Envío):** `Total xfer: 1.00x`.
        ![PC Log](img/9_sideload_pc_log.png)
    * **Móvil (Recepción):** `Install completed with status 0`.
        ![Phone Log](img/8_sideload_phone_log.jpg)

---

## 🏆 Resultado Final
El dispositivo opera con **Android 16** (LineageOS 23), libre de GApps (Google Apps) y servicios de Samsung.

> **Escritorio "Clean":**
> ![Home](img/10_home_screen.jpg)

> **Especificaciones Técnicas:**
> ![Specs](img/11_final_specs.png)

---
**✅ PROYECTO CERRADO EXITOSAMENTE**
