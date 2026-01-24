# 📱 POCO M5 - "El Atacante Rápido"
**Estado de la Misión:** 🟡 En Configuración (Fase 2)
**Objetivo:** Despliegue de Kali NetHunter Rootless

## 1. Conexión y Reconocimiento (ADB)
Para iniciar la auditoría, establecimos la conexión mediante el puente de depuración (ADB).

### 1.1 Autorización del Dispositivo
Tras activar las "Opciones de desarrollador" y la "Depuración USB", realizamos el handshake RSA.
- **Comando:** `./adb devices`
- **Resultado:** El dispositivo pasó de `unauthorized` a `device`, confirmando control total.

![Estado Device Autorizado](img/01-device.png)

### 1.2 Extracción de Ficha Técnica (Forensics)
En lugar de tomar notas manuales, realizamos un volcado completo de las propiedades del sistema (`build.prop`) para tener una referencia exacta del hardware y software.

- **Comando ejecutado:**
  ```powershell
  ./adb shell getprop > POCO_M5_specs.txt

![Ejecución...](img/02-volcado.png)
> **💡 ¿Qué hace este comando?**
> * **`adb shell`**: Abre una puerta para enviar órdenes directas al sistema operativo del móvil.
> * **`getprop`**: Abreviatura de *"Get Properties"* (Obtener Propiedades). Le pide al dispositivo su "ADN" completo: modelo de procesador, versión de seguridad, configuración de pantalla, etc.
> * **`>`**: Este símbolo es un **operador de redirección**. En lugar de escupir las miles de líneas de texto en la pantalla de la terminal, las "vuelca" silenciosamente dentro del archivo `.txt` para guardarlas como evidencia.

### 1.3 Verificación de la Evidencia
Se generó correctamente el archivo `POCO_M5_specs.txt` en el directorio de trabajo, conteniendo todas las flags del sistema (versión de SDK, configuración de Bluetooth, detalles del kernel, etc.).

![Archivo generado en Windows](img/03-archivo.png)
![Vista previa de los datos internos](img/04-vista%20informacion%20del%20movil.png)

---

## 2. Fase 2: Despliegue de Infraestructura (Kali NetHunter)

En esta fase transformamos el dispositivo de un teléfono estándar a una herramienta de auditoría. El objetivo es desplegar **Kali NetHunter Rootless**, una versión de la suite de pentesting diseñada para funcionar sobre una capa de abstracción sin modificar la partición del sistema (sin Root).

### 2.1 Arquitectura del Entorno
Para lograr la ejecución de herramientas Linux sobre Android sin privilegios de superusuario, dependemos de un entorno *chroot* (o *proot*) gestionado por un emulador de terminal.

* **Motor Base:** Termux.
* **Capa de Compatibilidad:** Proot-Distro (simula el acceso a directorios raíz).
* **Interfaz:** KeX (Kali Desktop Experience) para entorno gráfico o CLI para consola.

### 2.2 Selección de Fuentes de Software (Supply Chain Security)
Durante la planificación, se descartó el uso de *Google Play Store* para la obtención de herramientas críticas.

| Fuente | Estado | Decisión | Justificación Técnica |
| :--- | :--- | :--- | :--- |
| **Google Play** | ❌ Deprecated | **DESCARTADO** | La versión de Termux en Play Store no recibe actualizaciones debido a restricciones en la API de Android 10+ (targetSdkVersion). Su uso provoca fallos en la gestión de repositorios (`apt update`). |
| **F-Droid** | ✅ Active | **APROBADO** | Repositorio de Software Libre (FOSS). Garantiza binarios firmados por el desarrollador original y compatibilidad total con los scripts de instalación de NetHunter. |

---
### 2.3 Implementación de la Fuente Segura (F-Droid)
Procedemos a la instalación del cliente F-Droid para gestionar los paquetes de software libre necesarios para la auditoría.

**1. Obtención del Binario (Source Validation)**
Accedemos al portal oficial (`f-droid.org`) para descargar el paquete `.apk`. Esto garantiza la integridad del instalador y evita versiones adulteradas de terceros.

![Fuente Oficial](img/05-fdroid-source.png)

**2. Confirmación de Instalación**
El sistema solicita confirmación para desplegar el paquete. Al no provenir de Google Play, se valida manualmente el permiso de instalación.

![Instalación del APK](img/06-fdroid-install.png)

**3. Sincronización de Repositorios**
Tras el primer inicio, el cliente actualiza los índices de software (mirrors). La carga correcta de los iconos confirma que tenemos conexión segura con el repositorio FOSS y estamos listos para descargar Termux.

![F-Droid Operativo](img/07-fdroid-running.png)
