# 🛡️ Lab Deployment: BlackArch Linux — *The Smart Way* (via EndeavourOS)

> **⚠️ DISCLAIMER / AVISO LEGAL:**
> Este repositorio y su documentación han sido creados **exclusivamente con fines educativos y de investigación en Ciberseguridad**.  
> El autor no se hace responsable del uso indebido de las herramientas aquí descritas. El acceso a sistemas informáticos sin autorización es ilegal.
> *"Knowledge is power, but power requires responsibility."*

---

## 🎯 Objetivo del Proyecto

El propósito de este laboratorio es desplegar un **entorno de Pentesting robusto, estable y actualizado**, integrando el arsenal completo del **repositorio oficial de BlackArch Linux (+2800 herramientas)** sobre una base sólida de **EndeavourOS (Arch Linux)**.

Este proyecto documenta:
1.  El **fallo crítico** al intentar instalar la ISO oficial *Legacy* de BlackArch.
2.  El **troubleshooting real** del error de keyring/GPG.
3.  La **solución definitiva** mediante una arquitectura modular.

---

## 🚩 Fase 1: El Problema — *The Legacy ISO Fail*

Inicialmente se intentó desplegar la imagen oficial `blackarch-linux-slim-2023.05.01`. Al tratarse de una distribución *Rolling Release* congelada en el tiempo, surgieron conflictos críticos con las firmas digitales.

### 🧪 Análisis del Fallo

| Paso | Estado | Observación |
| :--- | :---: | :--- |
| Selección de ISO Slim | ✅ | Descarga correcta |
| Arranque Live (Boot) | ✅ | El sistema inicia bien |
| Lanzamiento Calamares | ✅ | La interfaz gráfica carga |
| **Instalación de Paquetes** | ❌ | **FALLO CRÍTICO** |

### 📸 Evidencia Visual del Error
1. **Selección de la Imagen:**
   ![Selección ISO](img/01_seleccion_iso_blackarch_slim.png)

2. **Arranque del Sistema:**
   ![Boot Menu](img/02_boot_menu_blackarch.png)

3. **Intento de Instalación:**
   ![Inicio Instalador](img/03_lanzamiento_instalador_legacy.png)

4. **El Bloqueo:**
   ![Proceso Fallido](img/04_proceso_instalacion_fallido.png)

5. **Diagnóstico Final (Keyring Error):**
   El gestor de paquetes `pacman` confirma que las llaves están corruptas o caducadas.
   ![Error Fatal](img/05_error_critico_pacman_keyring.png)

---

## 🛠️ Fase 2: La Solución — *Arquitectura Modular*

Para garantizar la estabilidad, cambiamos la estrategia: **"Instalar una base Arch Linux moderna (EndeavourOS) y luego inyectar el ADN de BlackArch"**.

### 🧩 Despliegue de la Base (EndeavourOS)
Se seleccionó EndeavourOS por su instalador maduro y su cercanía a Arch puro.

6. **Obtención de la Imagen:**
   ![Web Oficial](img/06_web_oficial_endeavouros.jpg)

7. **Configuración de Mirrors:**
   ![Mirrors](img/07_seleccion_mirror_descarga.png)
   ![Descarga](img/08_descarga_iso_endeavour.png)

8. **Arranque del Nuevo Motor:**
   ![Boot Endeavour](img/09_boot_menu_endeavouros.jpg)
   ![Entorno Live](img/10_entorno_live_endeavour.jpg)

9. **La Clave del Éxito (Modo Offline):**
   Se seleccionó la instalación **Offline** para desplegar el escritorio XFCE nativo desde la ISO, eliminando riesgos de red durante la instalación base.
   ![Installer](img/11_inicio_instalador_calamares.png)
   ![Modo Offline](img/12_seleccion_modo_offline_seguro.png)

10. **Primer Boot Exitoso:**
    ![Arranque Exitoso](img/13_primer_boot_exitoso_grub.jpg)

---

## ⚡ Fase 3: La Transformación — *BlackArch Strap*

Con el sistema base estable, procedemos a ejecutar el script oficial de integración `strap.sh`.

### 💻 Comandos de Integración
```bash
# 1. Descargar el script de integración
curl -O [https://blackarch.org/strap.sh](https://blackarch.org/strap.sh)

# 2. Dar permisos de ejecución
chmod +x strap.sh

# 3. Ejecutar la transformación (Root)
sudo ./strap.sh


