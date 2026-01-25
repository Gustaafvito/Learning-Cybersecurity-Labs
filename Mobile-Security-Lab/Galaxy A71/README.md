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
