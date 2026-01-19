# 📱 Análisis de Seguridad en Android & Simulación de Adversarios

## 🛡️ Descripción del Proyecto
Este laboratorio simula un escenario de **Red Team** y **Pentesting Móvil** para analizar la evolución de la seguridad en Android. El objetivo es comparar cómo las vulnerabilidades críticas en versiones antiguas (Android 8.1) han sido mitigadas en versiones modernas (Android 12+), y demostrar el riesgo de utilizar dispositivos desactualizados.

---

## 🏗️ Fase 1: Configuración del Entorno (Lab Setup)

Para realizar las pruebas de concepto (PoC) de manera segura, se ha configurado un entorno virtualizado aislado utilizando **Android Studio**.

### 1. Creación del Dispositivo Virtual (AVD)
Se utilizó el **Device Manager** de Android Studio para definir un nuevo objetivo.

![Crear Dispositivo](img/setup_1_creacion.png)

### 2. Selección de Hardware
Se eligió un perfil de **Pixel 2**. Este dispositivo es ideal para pruebas de seguridad estándar debido a su compatibilidad y especificaciones representativas de un dispositivo de gama media-alta de su época.

![Hardware Pixel 2](img/setup_2_hardware.png)

### 3. Selección del Sistema Operativo (Punto Crítico)
Esta es la decisión más importante del laboratorio. Se seleccionó explícitamente **Android 8.1 (Oreo) - API 27**.

* **¿Por qué API 27?**: Esta versión carece de las protecciones modernas de privacidad (como los indicadores visuales de cámara/micrófono o el bloqueo estricto de actividades en segundo plano) introducidas en Android 12 (API 31). Esto permite demostrar ataques de post-explotación con Metasploit que serían bloqueados en sistemas actuales.

![Selección de API 27](img/setup_3_sistema_operativo.png)

### 4. Despliegue del Objetivo
El dispositivo virtual se ejecuta exitosamente, simulando un teléfono funcional conectado a la red virtual del laboratorio, listo para recibir la auditoría.

![Dispositivo Corriendo](img/setup_4_ejecucion.png)

---
